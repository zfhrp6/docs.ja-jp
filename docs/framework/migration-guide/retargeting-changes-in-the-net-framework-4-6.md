---
title: ".NET Framework 4.6 における再ターゲットの変更点 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa849255-f90f-4bf1-b0ff-b173c12110d7
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# .NET Framework 4.6 における再ターゲットの変更点
まれに、変更を再ターゲットすると [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] を対象として再コンパイルされるアプリに影響する場合があります。 別途指定がない限り、これらの変更が、以前のバージョンの .NET Framework をターゲットとし、かつ [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] で実行されているバイナリに影響を与えることはありません。  
  
 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] には、次の領域の変更の再ターゲットが含まれます。  
  
-   [ASP.NET](#ASP)  
  
-   [ネットワーク](#Net)  
  
-   [Windows Communications Foundation \(WCF\)](#WCF)  
  
-   [Windows フォーム](#WinForms)  
  
-   [Windows Presentation Foundation \(WPF\)](#WPF)  
  
-   [XML](#XML)  
  
<a name="ASP"></a>   
## ASP.NET  
  
|機能|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|<xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName> の `tagKey` 値を使用する <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName>|HTML 標準に準拠して、<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName> メソッドは <xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName> を HTML 応答の非終了タグとしてレンダリングします。|これで、BR タグは 1 つの改行を生成します。 以前は 2 つの改行が生成されていました。<br /><br /> `<BR>` タグを使用して 2 つの改行を生成するアプリでは、<xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName> 引数を使用した <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName> メソッドの呼び出しを追加することで、以前の動作を復元できます。|マイナー|  
  
<a name="Net"></a>   
## ネットワーク  
  
|機能|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|<xref:System.Net.ServicePointManager?displayProperty=fullName> および <xref:System.Net.Security.SslStream?displayProperty=fullName>|.NET Framework 4.6 以降を対象とするアプリでは、<xref:System.Net.ServicePointManager?displayProperty=fullName> および <xref:System.Net.Security.SslStream?displayProperty=fullName> クラスで Tls1.0、Tls1.1、または Tls 1.2 の 3 つのプロトコルのいずれかを使用できます。<br /><br /> NET Framework の以前のバージョンを対象とするアプリは、NET Framework 4.6 上で実行する場合でも、影響を受けません。|この変更は、.NET Framework 4.6 を対象とし、SSL を使用して <xref:System.Net.Http.HttpClient>、<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>、<xref:System.Net.Mail.SmtpClient>、<xref:System.Net.Security.SslStream> のいずれかのタイプで HTTPS サーバーまたはソケット サーバーと対話するすべてのアプリに影響します。  詳細については、「[軽減策: TLS プロトコル](../../../docs/framework/migration-guide/mitigation-tls-protocols.md)」を参照してください。|マイナー|  
  
<a name="WCF"></a>   
## Windows Communications Foundation \(WCF\)  
  
|特性|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|<xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%2A?displayProperty=fullName>|`null` `authorizationPolicies` 引数を指定して <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> を呼び出したときに返される <xref:System.IdentityModel.Policy.AuthorizationContext> の実装が [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] で変更されました。|まれに、カスタム認証を使用する WCF アプリの動作に違いが生じる可能性があります。 以前の動作が必要な場合は、「[軽減策: 既定の AuthorizationContext](../../../docs/framework/migration-guide/mitigation-default-authorizationcontext.md)」をご覧ください。|マイナー|  
  
<a name="WinForms"></a>   
## Windows フォーム  
  
|機能|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName>|.NET Framework 4.6 以降を対象にしたアプリでは、<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> メソッドで、PNG フレームを含んだアイコンを正常に <xref:System.Drawing.Bitmap> オブジェクトに変換できます。<br /><br /> .NET Framework 4.5.2 以前のバージョンを対象としたアプリでは、<xref:System.Drawing.Icon> オブジェクトに PNG フレームが含まれていると、<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> メソッドが <xref:System.ArgumentOutOfRangeException> の例外をスローします。|この変更は、.NET Framework 4.6 を対象として再コンパイルされたアプリのうち、<xref:System.Drawing.Icon> オブジェクトに PNG フレームが含まれている場合は <xref:System.ArgumentOutOfRangeException> 例外をスローするように特別な処理を実行するアプリに影響します。 この動作が望ましくない場合、構成スイッチで以前の動作を復元します。 詳細については、「[軽減策: Icon オブジェクトの PNG フレーム](../../../docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md)」を参照してください。|マイナー|  
  
<a name="WPF"></a>   
## Windows Presentation Foundation \(WPF\)  
  
|機能|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|高 DPI でのレイアウトの丸め処理|余白、境界線、およびそれらの内部の背景の丸め処理の方法が変更されました。|WPF コントロールのレイアウトが若干変化する可能性があります。 詳細については、「[軽減策: WPF レイアウト](../../../docs/framework/migration-guide/mitigation-wpf-layout.md)」を参照してください。|マイナー|  
  
<a name="XML"></a>   
## XML  
  
|特性|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|XSD スキーマ検証|.NET Framework 4.6 以降では、複合キーが使用され、1 つのキーが空の場合、XSD スキーマ検証で一意制約の違反が検出されます。|「[軽減策: XML スキーマ検証](../../../docs/framework/migration-guide/mitigation-xml-schema-validation.md)」を参照してください。|マイナー|  
|<xref:System.Xml.XmlWriter>|.NET Framework 4.5.2 またはそれ以前のバージョンをターゲットとするアプリケーションの場合、例外フォールバック処理を使用した無効なサロゲート ペアを作成しても、必ず例外がスローされるとは限りません。<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] をターゲットとするアプリケーションでは、無効なサロゲート ペアを作成しようとすると、<xref:System.ArgumentException> の例外がスローされます。|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] をターゲットとするように再コンパイルされたアプリケーションが、無効なサロゲート ペアを作成すると、これまでスローされなかった例外がスローされるようになります。|エッジ|