---
title: "WIF セッション管理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98bce126-18a9-401b-b20d-67ee462a5f8a
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# WIF セッション管理
クライアントが最初に証明書利用者によってホスト保護されたリソースにアクセスしようとしたときに、クライアント証明書は、ユーザーによって信頼されるセキュリティ トークン Services \(STS\) に最初に認証する必要があります。  STS はクライアントに、セキュリティ トークンを発行します。  クライアントは、保護されているリソースへのクライアント アクセスを許可する証明書利用者にこのトークンを示します。  ただし、特に証明書利用者と同じコンピューターにまたは同じドメイン内に存在しない場合があるため、クライアントへの各要求に関する STS に再認証する側に必要です。  代わりに、Windows ID Foundation \(WIF\) は、クライアント証明書利用者にすべての要求の証明書利用者に認証にクライアントがセッションのセキュリティ トークンを後の最初の要求を使用するセッション設定されている。  証明書利用者はクッキー内に格納されているクライアントの <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName>を再度確立するためにこのセッションのセキュリティ トークンを使用できます。  
  
 STS は、認証を提供するクライアントがあるかを定義します。  ただし、クライアントが STS に認証できる複数の資格情報がある場合があります。  たとえば、Windows Live からトークン、ユーザー名とパスワード、および証明書 smartkey がある場合があります。  この場合、STS はクライアントに示す資格情報の 1 種類に対応するクライアントに各 ID を持つ複数の ID を与えます。  証明書利用者はクライアントに与えられる許可するアクセスのレベルを決定するときにこれらの ID を一つ以上使用できます。  
  
 <xref:System.IdentityModel.Tokens.SessionSecurityToken?displayProperty=fullName> がクライアントの <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName>を再確立するために使用されます。<xref:System.Security.Claims.ClaimsPrincipal.Identities%2A>でクライアント ID をすべて備えた。  コレクションの各 <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> は、その ID に関連付けられているブートストラップのトークンが含まれています。  
  
 新しいセッションのトークンが元のセッションのトークンのセッション ID に問題 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler?displayProperty=fullName> トークンは、キャッシュのセッションのトークンを更新しません。  一意のセッション ID を持つセッションのトークンを常にインスタンス化する必要があります  
  
> [!NOTE]
>  Session.SecurityTokenHandler.ReadToken は無効な入力を受け取る場合は <xref:System.Xml.XmlException> の例外をスローします; たとえば、セッションのトークンを含むクッキーの破損。  この例外をキャッチする推奨し、アプリケーション固有の動作を提供します。  
  
 保護された Web ページが保護されたドメインにあるリソースの多くが含まれている場合、グラフィックスなど\) は、クライアント証明書利用者にこれらのリソースをダウンロードするに再認証する必要があります。  セッションの認証トークンの使用は、要求ごとの STS に認証する必要はありませんが、多くのクッキーが送信されることを意味します。まだ  マイナー項目が保護されていないドメインに格納され、メイン Web ページからリンク間に、重要なデータやリソースが保護されたドメインに格納するために Web ページを設定することがあります。  また、保護されたドメインだけを参照するようにクッキーのパスを設定します。  
  
 参照モードで動作するように、マイクロソフトは、ハンドラーを **global.asax.cs** ファイルの <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SessionSecurityTokenCreated> のイベントに提供し、<xref:System.IdentityModel.Services.SessionSecurityTokenCreatedEventArgs.SessionToken%2A> のプロパティに渡されるトークンで **IsReferenceMode** のプロパティを設定することをお勧めします。  これらの更新はセッションのトークンを要求ごとの参照モードで動作し、のみセッションの認証モジュールの <xref:System.IdentityModel.Services.SessionAuthenticationModule.IsReferenceMode%2A> のプロパティを設定することでサポートされていることを確認します。  
  
## 機能拡張  
 セッション管理機構を拡張できます。  このの 1 種類の理由は、パフォーマンスを向上させることです。  たとえば、メモリの状態間のセッションのセキュリティ トークンを示しますがクッキーになる変換するか、最適化するクッキーのカスタム ハンドラーを作成できます。  そのためには、<xref:System.IdentityModel.Services.CookieHandler?displayProperty=fullName>から派生したカスタムのクッキーのハンドラーを使用するように <xref:System.IdentityModel.Services.SessionAuthenticationModule?displayProperty=fullName> の <xref:System.IdentityModel.Services.SessionAuthenticationModule.CookieHandler%2A?displayProperty=fullName> のプロパティを構成できます。  <xref:System.IdentityModel.Services.ChunkedCookieHandler?displayProperty=fullName> は、クッキーのハイパーテキスト転送プロトコル \(HTTP\) に対する許容サイズを超えるため、既定のクッキーのハンドラーです; カスタムのクッキーのハンドラーを使用すると、chunking を実装する必要があります。  
  
 詳細については、" [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) " \(http:\/\/go.microsoft.com\/fwlink\/?LinkID\=248408\) のサンプル。  この例は、参照によって大きいクッキーを交換する代わりに、セッションを使用できるように準備完了ファームにセッション キャッシュを示します \(tokenreplycache ではなく\) ; このサンプルには、ファームのクッキーを保護する簡単な方法を示します。  セッション キャッシュは、WCF ベースです。  保護しているセッションに関連するサンプルは、web.config の適切なスニペットを単純に貼り付けてアクティブにできる MachineKey に基づいて、クッキーの変換の WIF 4.5 の新機能について示します。  サンプル自体は「されませんが」、ファームのファーム アプリケーションを準備完了ようにするために必要な情報を示します。