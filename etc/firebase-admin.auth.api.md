## API Report File for "firebase-admin.auth"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts

/// <reference types="node" />

import { Agent } from 'http';

// @public
export interface ActionCodeSettings {
    android?: {
        packageName: string;
        installApp?: boolean;
        minimumVersion?: string;
    };
    dynamicLinkDomain?: string;
    handleCodeInApp?: boolean;
    iOS?: {
        bundleId: string;
    };
    url: string;
}

// @public
export interface AllowByDefault {
    disallowedRegions: string[];
}

// @public
export interface AllowByDefaultWrap {
    allowByDefault: AllowByDefault;
    // @alpha (undocumented)
    allowlistOnly?: never;
}

// @public
export interface AllowlistOnly {
    allowedRegions: string[];
}

// @public
export interface AllowlistOnlyWrap {
    // @alpha (undocumented)
    allowByDefault?: never;
    allowlistOnly: AllowlistOnly;
}

// @public
export class Auth extends BaseAuth {
    // Warning: (ae-forgotten-export) The symbol "App" needs to be exported by the entry point index.d.ts
    get app(): App;
    projectConfigManager(): ProjectConfigManager;
    tenantManager(): TenantManager;
}

// @public
export type AuthFactorType = 'phone';

// @public
export type AuthProviderConfig = SAMLAuthProviderConfig | OIDCAuthProviderConfig;

// @public
export interface AuthProviderConfigFilter {
    maxResults?: number;
    pageToken?: string;
    type: 'saml' | 'oidc';
}

// @public
export abstract class BaseAuth {
    createCustomToken(uid: string, developerClaims?: object): Promise<string>;
    createProviderConfig(config: AuthProviderConfig): Promise<AuthProviderConfig>;
    createSessionCookie(idToken: string, sessionCookieOptions: SessionCookieOptions): Promise<string>;
    createUser(properties: CreateRequest): Promise<UserRecord>;
    deleteProviderConfig(providerId: string): Promise<void>;
    deleteUser(uid: string): Promise<void>;
    deleteUsers(uids: string[]): Promise<DeleteUsersResult>;
    generateEmailVerificationLink(email: string, actionCodeSettings?: ActionCodeSettings): Promise<string>;
    generatePasswordResetLink(email: string, actionCodeSettings?: ActionCodeSettings): Promise<string>;
    generateSignInWithEmailLink(email: string, actionCodeSettings: ActionCodeSettings): Promise<string>;
    generateVerifyAndChangeEmailLink(email: string, newEmail: string, actionCodeSettings?: ActionCodeSettings): Promise<string>;
    getProviderConfig(providerId: string): Promise<AuthProviderConfig>;
    getUser(uid: string): Promise<UserRecord>;
    getUserByEmail(email: string): Promise<UserRecord>;
    getUserByPhoneNumber(phoneNumber: string): Promise<UserRecord>;
    getUserByProviderUid(providerId: string, uid: string): Promise<UserRecord>;
    getUsers(identifiers: UserIdentifier[]): Promise<GetUsersResult>;
    importUsers(users: UserImportRecord[], options?: UserImportOptions): Promise<UserImportResult>;
    listProviderConfigs(options: AuthProviderConfigFilter): Promise<ListProviderConfigResults>;
    listUsers(maxResults?: number, pageToken?: string): Promise<ListUsersResult>;
    revokeRefreshTokens(uid: string): Promise<void>;
    setCustomUserClaims(uid: string, customUserClaims: object | null): Promise<void>;
    updateProviderConfig(providerId: string, updatedConfig: UpdateAuthProviderRequest): Promise<AuthProviderConfig>;
    updateUser(uid: string, properties: UpdateRequest): Promise<UserRecord>;
    // @alpha (undocumented)
    _verifyAuthBlockingToken(token: string, audience?: string): Promise<DecodedAuthBlockingToken>;
    verifyIdToken(idToken: string, checkRevoked?: boolean): Promise<DecodedIdToken>;
    verifySessionCookie(sessionCookie: string, checkRevoked?: boolean): Promise<DecodedIdToken>;
}

// @public
export interface BaseAuthProviderConfig {
    displayName?: string;
    enabled: boolean;
    providerId: string;
}

// @public
export interface BaseCreateMultiFactorInfoRequest {
    displayName?: string;
    factorId: string;
}

// @public
export interface BaseUpdateMultiFactorInfoRequest {
    displayName?: string;
    enrollmentTime?: string;
    factorId: string;
    uid?: string;
}

// @public
export type CreateMultiFactorInfoRequest = CreatePhoneMultiFactorInfoRequest;

// @public
export interface CreatePhoneMultiFactorInfoRequest extends BaseCreateMultiFactorInfoRequest {
    phoneNumber: string;
}

// @public
export interface CreateRequest extends UpdateRequest {
    multiFactor?: MultiFactorCreateSettings;
    uid?: string;
}

// @public
export type CreateTenantRequest = UpdateTenantRequest;

// @alpha (undocumented)
export interface DecodedAuthBlockingToken {
    // (undocumented)
    [key: string]: any;
    // (undocumented)
    aud: string;
    // (undocumented)
    event_id: string;
    // (undocumented)
    event_type: string;
    // (undocumented)
    exp: number;
    // (undocumented)
    iat: number;
    // (undocumented)
    ip_address: string;
    // (undocumented)
    iss: string;
    // (undocumented)
    locale?: string;
    // (undocumented)
    oauth_access_token?: string;
    // (undocumented)
    oauth_expires_in?: number;
    // (undocumented)
    oauth_id_token?: string;
    // (undocumented)
    oauth_refresh_token?: string;
    // (undocumented)
    oauth_token_secret?: string;
    // (undocumented)
    raw_user_info?: string;
    // (undocumented)
    sign_in_attributes?: {
        [key: string]: any;
    };
    // (undocumented)
    sign_in_method?: string;
    // (undocumented)
    sub: string;
    // (undocumented)
    tenant_id?: string;
    // (undocumented)
    user_agent?: string;
    // Warning: (ae-forgotten-export) The symbol "DecodedAuthBlockingUserRecord" needs to be exported by the entry point index.d.ts
    //
    // (undocumented)
    user_record?: DecodedAuthBlockingUserRecord;
}

// @public
export interface DecodedIdToken {
    [key: string]: any;
    aud: string;
    auth_time: number;
    email?: string;
    email_verified?: boolean;
    exp: number;
    firebase: {
        identities: {
            [key: string]: any;
        };
        sign_in_provider: string;
        sign_in_second_factor?: string;
        second_factor_identifier?: string;
        tenant?: string;
        [key: string]: any;
    };
    iat: number;
    iss: string;
    phone_number?: string;
    picture?: string;
    sub: string;
    uid: string;
}

// @public
export interface DeleteUsersResult {
    // Warning: (ae-forgotten-export) The symbol "FirebaseArrayIndexError" needs to be exported by the entry point index.d.ts
    errors: FirebaseArrayIndexError[];
    failureCount: number;
    successCount: number;
}

// @public
export interface EmailIdentifier {
    // (undocumented)
    email: string;
}

// @public
export interface EmailSignInProviderConfig {
    enabled: boolean;
    passwordRequired?: boolean;
}

// @public
export function getAuth(app?: App): Auth;

// @public
export interface GetUsersResult {
    notFound: UserIdentifier[];
    users: UserRecord[];
}

// @public (undocumented)
export type HashAlgorithmType = 'SCRYPT' | 'STANDARD_SCRYPT' | 'HMAC_SHA512' | 'HMAC_SHA256' | 'HMAC_SHA1' | 'HMAC_MD5' | 'MD5' | 'PBKDF_SHA1' | 'BCRYPT' | 'PBKDF2_SHA256' | 'SHA512' | 'SHA256' | 'SHA1';

// @public
export interface ListProviderConfigResults {
    pageToken?: string;
    providerConfigs: AuthProviderConfig[];
}

// @public
export interface ListTenantsResult {
    pageToken?: string;
    tenants: Tenant[];
}

// @public
export interface ListUsersResult {
    pageToken?: string;
    users: UserRecord[];
}

// @public
export interface MultiFactorConfig {
    factorIds?: AuthFactorType[];
    state: MultiFactorConfigState;
}

// @public
export type MultiFactorConfigState = 'ENABLED' | 'DISABLED';

// @public
export interface MultiFactorCreateSettings {
    enrolledFactors: CreateMultiFactorInfoRequest[];
}

// @public
export abstract class MultiFactorInfo {
    readonly displayName?: string;
    readonly enrollmentTime?: string;
    readonly factorId: string;
    toJSON(): object;
    readonly uid: string;
}

// @public
export class MultiFactorSettings {
    enrolledFactors: MultiFactorInfo[];
    toJSON(): object;
}

// @public
export interface MultiFactorUpdateSettings {
    enrolledFactors: UpdateMultiFactorInfoRequest[] | null;
}

// @public
export interface OAuthResponseType {
    code?: boolean;
    idToken?: boolean;
}

// @public
export interface OIDCAuthProviderConfig extends BaseAuthProviderConfig {
    clientId: string;
    clientSecret?: string;
    issuer: string;
    responseType?: OAuthResponseType;
}

// @public
export interface OIDCUpdateAuthProviderRequest {
    clientId?: string;
    clientSecret?: string;
    displayName?: string;
    enabled?: boolean;
    issuer?: string;
    responseType?: OAuthResponseType;
}

// @public
export interface PhoneIdentifier {
    // (undocumented)
    phoneNumber: string;
}

// @public
export class PhoneMultiFactorInfo extends MultiFactorInfo {
    readonly phoneNumber: string;
    toJSON(): object;
}

// @public
export class ProjectConfig {
    readonly smsRegionConfig?: SmsRegionConfig;
    toJSON(): object;
}

// @public
export class ProjectConfigManager {
    getProjectConfig(): Promise<ProjectConfig>;
    updateProjectConfig(projectConfigOptions: UpdateProjectConfigRequest): Promise<ProjectConfig>;
}

// @public
export interface ProviderIdentifier {
    // (undocumented)
    providerId: string;
    // (undocumented)
    providerUid: string;
}

// @public
export interface SAMLAuthProviderConfig extends BaseAuthProviderConfig {
    callbackURL?: string;
    idpEntityId: string;
    rpEntityId: string;
    ssoURL: string;
    x509Certificates: string[];
}

// @public
export interface SAMLUpdateAuthProviderRequest {
    callbackURL?: string;
    displayName?: string;
    enabled?: boolean;
    idpEntityId?: string;
    rpEntityId?: string;
    ssoURL?: string;
    x509Certificates?: string[];
}

// @public
export interface SessionCookieOptions {
    expiresIn: number;
}

// @public
export type SmsRegionConfig = AllowByDefaultWrap | AllowlistOnlyWrap;

// @public
export class Tenant {
    // (undocumented)
    readonly anonymousSignInEnabled: boolean;
    readonly displayName?: string;
    get emailSignInConfig(): EmailSignInProviderConfig | undefined;
    get multiFactorConfig(): MultiFactorConfig | undefined;
    readonly smsRegionConfig?: SmsRegionConfig;
    readonly tenantId: string;
    readonly testPhoneNumbers?: {
        [phoneNumber: string]: string;
    };
    toJSON(): object;
}

// @public
export class TenantAwareAuth extends BaseAuth {
    createSessionCookie(idToken: string, sessionCookieOptions: SessionCookieOptions): Promise<string>;
    readonly tenantId: string;
    verifyIdToken(idToken: string, checkRevoked?: boolean): Promise<DecodedIdToken>;
    verifySessionCookie(sessionCookie: string, checkRevoked?: boolean): Promise<DecodedIdToken>;
}

// @public
export class TenantManager {
    authForTenant(tenantId: string): TenantAwareAuth;
    createTenant(tenantOptions: CreateTenantRequest): Promise<Tenant>;
    deleteTenant(tenantId: string): Promise<void>;
    getTenant(tenantId: string): Promise<Tenant>;
    listTenants(maxResults?: number, pageToken?: string): Promise<ListTenantsResult>;
    updateTenant(tenantId: string, tenantOptions: UpdateTenantRequest): Promise<Tenant>;
}

// @public
export interface UidIdentifier {
    // (undocumented)
    uid: string;
}

// @public (undocumented)
export type UpdateAuthProviderRequest = SAMLUpdateAuthProviderRequest | OIDCUpdateAuthProviderRequest;

// @public
export type UpdateMultiFactorInfoRequest = UpdatePhoneMultiFactorInfoRequest;

// @public
export interface UpdatePhoneMultiFactorInfoRequest extends BaseUpdateMultiFactorInfoRequest {
    phoneNumber: string;
}

// @public
export interface UpdateProjectConfigRequest {
    smsRegionConfig?: SmsRegionConfig;
}

// @public
export interface UpdateRequest {
    disabled?: boolean;
    displayName?: string | null;
    email?: string;
    emailVerified?: boolean;
    multiFactor?: MultiFactorUpdateSettings;
    password?: string;
    phoneNumber?: string | null;
    photoURL?: string | null;
    providersToUnlink?: string[];
    providerToLink?: UserProvider;
}

// @public
export interface UpdateTenantRequest {
    anonymousSignInEnabled?: boolean;
    displayName?: string;
    emailSignInConfig?: EmailSignInProviderConfig;
    multiFactorConfig?: MultiFactorConfig;
    smsRegionConfig?: SmsRegionConfig;
    testPhoneNumbers?: {
        [phoneNumber: string]: string;
    } | null;
}

// @public
export type UserIdentifier = UidIdentifier | EmailIdentifier | PhoneIdentifier | ProviderIdentifier;

// @public
export interface UserImportOptions {
    hash: {
        algorithm: HashAlgorithmType;
        key?: Buffer;
        saltSeparator?: Buffer;
        rounds?: number;
        memoryCost?: number;
        parallelization?: number;
        blockSize?: number;
        derivedKeyLength?: number;
    };
}

// @public
export interface UserImportRecord {
    customClaims?: {
        [key: string]: any;
    };
    disabled?: boolean;
    displayName?: string;
    email?: string;
    emailVerified?: boolean;
    metadata?: UserMetadataRequest;
    multiFactor?: MultiFactorUpdateSettings;
    passwordHash?: Buffer;
    passwordSalt?: Buffer;
    phoneNumber?: string;
    photoURL?: string;
    providerData?: UserProviderRequest[];
    tenantId?: string;
    uid: string;
}

// @public
export interface UserImportResult {
    errors: FirebaseArrayIndexError[];
    failureCount: number;
    successCount: number;
}

// @public
export class UserInfo {
    readonly displayName: string;
    readonly email: string;
    readonly phoneNumber: string;
    readonly photoURL: string;
    readonly providerId: string;
    toJSON(): object;
    readonly uid: string;
}

// @public
export class UserMetadata {
    readonly creationTime: string;
    readonly lastRefreshTime?: string | null;
    readonly lastSignInTime: string;
    toJSON(): object;
}

// @public
export interface UserMetadataRequest {
    creationTime?: string;
    lastSignInTime?: string;
}

// @public
export interface UserProvider {
    displayName?: string;
    email?: string;
    phoneNumber?: string;
    photoURL?: string;
    providerId?: string;
    uid?: string;
}

// @public
export interface UserProviderRequest {
    displayName?: string;
    email?: string;
    phoneNumber?: string;
    photoURL?: string;
    providerId: string;
    uid: string;
}

// @public
export class UserRecord {
    readonly customClaims?: {
        [key: string]: any;
    };
    readonly disabled: boolean;
    readonly displayName?: string;
    readonly email?: string;
    readonly emailVerified: boolean;
    readonly metadata: UserMetadata;
    readonly multiFactor?: MultiFactorSettings;
    readonly passwordHash?: string;
    readonly passwordSalt?: string;
    readonly phoneNumber?: string;
    readonly photoURL?: string;
    readonly providerData: UserInfo[];
    readonly tenantId?: string | null;
    toJSON(): object;
    readonly tokensValidAfterTime?: string;
    readonly uid: string;
}

```
