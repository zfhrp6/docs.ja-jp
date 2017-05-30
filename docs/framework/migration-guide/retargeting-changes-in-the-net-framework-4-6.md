---
title: ".NET Framework 4.6 における再ターゲットの変更点 | Microsoft ドキュメント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes, .NET Framework
- retargeting changes, .NET Framework 4.6
- application compatibility
ms.assetid: fa849255-f90f-4bf1-b0ff-b173c12110d7
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 19ad80233a79a4fdef89550696c1c3d33e14b355
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="retargeting-changes-in-the-net-framework-46"></a>.NET Framework 4.6 における再ターゲットの変更点
まれに、変更を再ターゲットすると [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] を対象として再コンパイルされるアプリに影響する場合があります。 別途指定がない限り、これらの変更が、以前のバージョンの .NET Framework をターゲットとし、かつ [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] で実行されているバイナリに影響を与えることはありません。  
  
 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] には、次の領域の変更の再ターゲットが含まれます。  
  
-   [コア](#Core)  
  
-   [ASP.NET](#ASP)  
  
-   [ネットワーク](#Net)  
  
-   [Windows Communications Foundation (WCF)](#WCF)  
  
-   [Windows フォーム](#WinForms)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [XML](#XML)  
  
<a name="Core"></a>   
## <a name="core"></a>コア  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>、<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>、および <xref:System.Threading.Tasks.Task> と <xref:System.Threading.Tasks.Task%601> を使ったタスク ベースの非同期操作|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 以降のバージョンを対象とするアプリの場合、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> はスレッドの <xref:System.Threading.ExecutionContext> に格納され、非同期操作全体にフローします。|<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> プロパティと <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> プロパティへの変更は、続いて起動される非同期タスクに反映されます。 詳細については、「[Mitigation: Culture and Asynchronous Operations (軽減策: カルチャお よび非同期操作)](../../../docs/framework/migration-guide/mitigation-culture-and-asynchronous-operations.md)」を参照してください。|マイナー|  
  
<a name="ASP"></a>   
## <a name="aspnet"></a>ASP.NET  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName> の `tagKey` 値を使用する <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName>|<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName> メソッドは、HTML 標準に準拠して <xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName> を HTML 応答の非終了タグとしてレンダリングします。|これで、BR タグは 1 つの改行を生成します。 以前は 2 つの改行が生成されていました。<br /><br /> `<BR>` タグを使用して 2 つの改行を生成するアプリでは、<xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName> 引数を使用した <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName> メソッドの呼び出しを追加することで、以前の動作を復元できます。|マイナー|  
  
<a name="Net"></a>   
## <a name="networking"></a>ネットワーク  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Net.ServicePointManager?displayProperty=fullName> および <xref:System.Net.Security.SslStream?displayProperty=fullName>|.NET Framework 4.6 以降を対象とするアプリでは、<xref:System.Net.ServicePointManager?displayProperty=fullName> および <xref:System.Net.Security.SslStream?displayProperty=fullName> クラスで Tls1.0、Tls1.1、または Tls 1.2 の 3 つのプロトコルのいずれかを使用できます。<br /><br /> NET Framework の以前のバージョンを対象とするアプリは、NET Framework 4.6 上で実行する場合でも、影響を受けません。|この変更は、.NET Framework 4.6 を対象とし、SSL を使用して <xref:System.Net.Http.HttpClient>、<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>、<xref:System.Net.Mail.SmtpClient>、<xref:System.Net.Security.SslStream> のいずれかのタイプで HTTPS サーバーまたはソケット サーバーと対話するすべてのアプリに影響します。  詳細については、「[軽減策: TLS プロトコル](../../../docs/framework/migration-guide/mitigation-tls-protocols.md)」を参照してください。|マイナー|  
  
<a name="WCF"></a>   
## <a name="windows-communications-foundation-wcf"></a>Windows Communications Foundation (WCF)  
  
|特性|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%2A?displayProperty=fullName>|`null``authorizationPolicies` 引数を指定して <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> を呼び出したときに返される <xref:System.IdentityModel.Policy.AuthorizationContext> の実装が [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] で変更されました。|まれに、カスタム認証を使用する WCF アプリの動作に違いが生じる可能性があります。 以前の動作が必要な場合は、「[軽減策: 既定のAuthorizationContext](../../../docs/framework/migration-guide/mitigation-default-authorizationcontext.md)」参照してください。|マイナー|  
  
<a name="WinForms"></a>   
## <a name="windows-forms"></a>Windows フォーム  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName>|.NET Framework 4.6 以降を対象にしたアプリでは、<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> メソッドで、PNG フレームを含んだアイコンを正常に <xref:System.Drawing.Bitmap> オブジェクトに変換できます。<br /><br /> .NET Framework 4.5.2 以前のバージョンを対象としたアプリでは、<xref:System.Drawing.Icon> オブジェクトに PNG フレームが含まれていると、<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> メソッドが <xref:System.ArgumentOutOfRangeException> の例外をスローします。|この変更は、.NET Framework 4.6 を対象として再コンパイルされたアプリのうち、<xref:System.Drawing.Icon> オブジェクトに PNG フレームが含まれている場合は <xref:System.ArgumentOutOfRangeException> 例外をスローするように特別な処理を実行するアプリに影響します。 この動作が望ましくない場合、構成スイッチで以前の動作を復元します。 詳細については、「[軽減策: Icon オブジェクトの PNG フレーム](../../../docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md)」を参照してください。|マイナー|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> および <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>|.NET Framework 4.6 と .NET Framework 4.6.1 を対象とするアプリでは、<xref:System.Windows.Threading.Dispatcher> 内で <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> プロパティ、または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> プロパティに対して加えられた変更は、ディスパッチャー操作の最後に失われます。 同様に、ディスパッチャー操作の外部で <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> に加えられた変更は、その操作の実行時には反映されない場合があります。|<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> プロパティと <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> プロパティに加えられた変更は、WPF UI コールバックと WPF アプリケーション内の他のコードとの間でフローされない場合があります。 詳細については、「[Mitigation: Culture and Dispatcher Operations in WPF Apps (軽減策: WPF アプリのカルチャおよびディスパッチャー操作)](../../../docs/framework/migration-guide/mitigation-culture-and-dispatcher-operations-in-wpf-apps.md)」を参照してください。|マイナー|  
|高 DPI でのレイアウトの丸め処理|余白、境界線、およびそれらの内部の背景の丸め処理の方法が変更されました。|WPF コントロールのレイアウトが若干変化する可能性があります。 詳細については、「[軽減策: WPF レイアウト](../../../docs/framework/migration-guide/mitigation-wpf-layout.md)」を参照してください。|マイナー|  
  
<a name="XML"></a>   
## <a name="xml"></a>XML  
  
|特性|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|XSD スキーマ検証|.NET Framework 4.6 以降では、複合キーが使用され、1 つのキーが空の場合、XSD スキーマ検証で一意制約の違反が検出されます。|「[軽減策: XML スキーマ検証](../../../docs/framework/migration-guide/mitigation-xml-schema-validation.md)」を参照してください。|マイナー|  
|<xref:System.Xml.XmlWriter>|.NET Framework 4.5.2 またはそれ以前のバージョンをターゲットとするアプリケーションの場合、例外フォールバック処理を使用した無効なサロゲート ペアを作成しても、必ず例外がスローされるとは限りません。<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] をターゲットとするアプリケーションでは、無効なサロゲート ペアを作成しようとすると、<xref:System.ArgumentException> の例外がスローされます。|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] をターゲットとするように再コンパイルされたアプリケーションが、無効なサロゲート ペアを作成すると、これまでスローされなかった例外がスローされるようになります。|エッジ|
