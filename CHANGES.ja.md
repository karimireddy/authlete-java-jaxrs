変更点
======

2.12 (2018 年 10 月 10 日)
--------------------------

- `AuthleteApiImpl` クラス
    * `getTokenList` メソッド群を実装。

- `pom.xml`
    * `authlete-java-common` のバージョンを 2.23 から 2.30 へ更新。
    * `gson` のバージョンを 2.6.2 から 2.8.5 へ更新。


2.11 (2018 年 09 月 11 日)
--------------------------

- `AuthleteApiImpl` クラス
    * `getJaxRsClientBuilder()` メソッドを追加。
    * `setJaxRsClientBuilder(ClientBuilder)` メソッドを追加。

- `pom.xml`
    * `javax.ws.rs-api` のバージョンを 2.0 から 2.1 へ更新。


2.10 (2018 年 07 月 21 日)
--------------------------

- `authlete-java-common` ライブラリ
    * バージョン 2.18 から 2.23 へ更新

- `AuthleteApiImpl` クラス
    * `registerClient(ClientRegistrationRequest)` メソッドを実装。
    * `verifyJose(JoseVerifyRequest)` メソッドを実装。


2.9 (2018 年 05 月 26 日)
-------------------------

- `HeaderClientCertificateExtractor` クラス
    * 正しく設定されていない Apache サーバーから送られてくる誤った `X-SSl-Cert[-*]`
      ヘッダーを無視するよう、 `extractClientCertificateChain()` メソッドの実装を更新。


2.8 (2018 年 05 月 09 日)
-------------------------

- `BaseEndpoint` クラス
    * `onError(WebApplicationException)` メソッドの実装を若干変更。古い実装では
      `exception.printStackTrace()` を呼んでいたが、新しい実装は何もしない。
    * `extractClientCertificateChain(HttpServletRequest)` メソッドを追加。
    * `extractClientCertificate(HttpServletRequest)` メソッドを追加。

- `BaseResourceEndpoint` クラス
    * `String clientCertificate` を 5 番目の引数として取る `validateAccessToken()`
      メソッドのバリアントを追加。

- `BaseTokenEndpoint` クラス
    * 5 つの引数を取る `handle()` メソッドのバリアントを追加。

- `TokenRequestHandler` クラス
    * 3 つの引数を取る `handle()` メソッドのバリアントを追加。

- 新しい部品
    * `ClientCertificateExtractor` インターフェース
    * `HeaderClientCertificateExtractor` クラス
    * `HttpsRequestClientCertificateExtractor` クラス

- authlete-java-common のバージョンを 2.18 に更新し、 `AuthleteApiImpl`
　もそれに合わせて更新。


2.7 (2017 年 12 月 08 日)
-------------------------

- `RevocationRequestHandler` 内の不具合を修正。 `/api/auth/revocation` API
  からのレスポンスに含まれる `action` レスポンスパラメーターの値が `OK` の場合、
  リボケーションエンドポイントからクライアントアプリケーションに返すレスポンスの
  Content-Type は `application/json` ではなく `application/javascript`
  であるべき。


2.6 (2017 年 11 月 20 日)
-------------------------

- `JaxRsUtils` クラスを追加。


2.5 (2017 年 11 月 16 日)
-------------------------

- authlete-java-common のバージョンを 2.11 に更新。

- authlete-java-common-2.11 で追加された新しい `AuthleteApi` メソッド群を実装。


2.4 (2017 年 10 月 18 日)
-------------------------

- authlete-java-common のバージョンを 2.10 に更新。

- `Settings.setReadTimeout(int)` メソッドをサポート。


2.3 (2017 年 10 月 13 日)
-------------------------

- authlete-java-common のバージョンを 2.9 に更新。

- `AuthleteApi.getSettings()` メソッドを実装。


2.2 (2017 年 07 月 21 日)
-------------------------

- authlete-java-common のバージョンを 2.7 に更新。

- `AuthleteApi.standardIntrospection(StandardIntrospectionRequest)`
  メソッドを実装。

- `BaseIntrospectionEndpoint` クラスと `IntrospectionRequestHandler`
  クラスを追加。


2.1 (2017 年 07 月 10 日)
-------------------------

- ユーザー認証時刻を秒ではなくミリ秒で扱っていた不具合を修正。


2.0 (2017 年 03 月 18 日)
-------------------------

- authlete-java-common のバージョンを 2.1 に更新。

- `AuthleteApi` インターフェースの新しいメソッド群を実装。
    * `deleteClientAuthorization(long, String)`
    * `getClientAuthorizationList(ClientAuthorizationGetListRequest)`
    * `updateClientAuthorization(long, ClientAuthorizationUpdateRequest)`


1.8 (2017 年 02 月 17 日)
-------------------------

- authlete-java-common のバージョンを 1.40 に更新。

- `AuthleteApi` インターフェースの `deleteGrantedScopes(long, String)`
  メソッドを実装。


1.7 (2017 年 02 月 15 日)
-------------------------

- `Response.hasEntity()` が投げる可能性のある `IllegalStateException` を
  キャッチするように `AuthleteApiImpl` を修正。


1.6 (2017 年 02 月 14 日)
-------------------------

- authlete-java-common のバージョンを 1.39 に更新。

- `AuthleteApi` インターフェースの `getGrantedScopes(long, String)`
  メソッドを実装。


1.5 (2017 年 02 月 03 日)
-------------------------

- `AuthleteApiImpl` で定義されている `callPostApi()` メソッド内の
  `application/json` を `application/json;UTF-8` に変更。


1.4 (2016 年 07 月 30 日)
-------------------------

- `AuthorizationDecisionHandlerSpi`, `AuthorizationRequestHandlerSpi` に
  `getScopes()` メソッドを追加。スコープを置き換える機能を提供するため。

- `AuthleteApi` バージョン 1.34 に適合するように `AuthleteApiImpl` を更新。


1.3 (2016 年 04 月 25 日)
-------------------------

- アクセストークンにプロパティー群を関連づける仕組みをサポートするため、
  `AuthorizationDecisionHandlerSpi`, `AuthorizationRequestHandlerSpi`,
  `TokenRequestHandlerSpi` に `getProperties()` メソッドを追加。

- `AccessTokenInfo` クラスに、`getProperties()` メソッド、
  `setProperties(Property[])` メソッド、その他のセッターメソッド群を追加。


1.2 (2016 年 02 月 08 日)
-------------------------

- `Base*Endpoint` クラス群を追加。

- アクセストークンの有効性を調べるためのクラス群を追加。

- ユーザー情報エンドポイントを実装するためのユーティリティークラス群を追加。


1.1 (2016 年 02 月 06 日)
-------------------------

- (a) JWK Set エンドポイント、(b) 設定エンドポイント、
  (c) 取り消しエンドポイントを実装するためのユーティリティークラス群を追加。

- `AuthleteApi` バージョン 1.28 に適合するように `AuthleteApiImpl` を更新。


1.0 (2016 年 01 月 11 日)
-------------------------

- 最初のリリース
