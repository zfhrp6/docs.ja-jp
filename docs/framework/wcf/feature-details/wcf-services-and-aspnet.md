---
title: WCF サービスと ASP.NET
ms.date: 03/30/2017
ms.assetid: b980496a-f0b0-4319-8e55-a0f0fa32da70
ms.openlocfilehash: 6cfd4f8a5dc2a7835cba409a37b09166e49e8df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506164"
---
# <a name="wcf-services-and-aspnet"></a>WCF サービスと ASP.NET
このトピックでは、ホスト Windows Communication Foundation (WCF) サービス サイド バイ サイド ASP.NET と ASP.NET 互換モードでのホストを使用について説明します。  
  
## <a name="hosting-wcf-side-by-side-with-aspnet"></a>WCF を ASP.NET とサイド バイ サイドでホストする方法  
 インターネット インフォメーション サービス (IIS) でホストされる WCF サービスで配置することができます。ASPX ページと 1 つの一般的なアプリケーション ドメイン内での ASMX Web サービス。 ASP.NET では、AppDomain の管理と WCF と ASP.NET HTTP ランタイムの両方の動的コンパイルなどの一般的なインフラストラクチャ サービスを提供します。 WCF の既定の構成は、サイド バイ サイド ASP.NET を使用します。  
  
 ![WCF サービスと ASP .NET: 状態の共有](../../../../docs/framework/wcf/feature-details/media/hostingwcfwithaspnet.gif "HostingWCFwithASPNET")  
  
 ASP.NET HTTP ランタイムは、ASP.NET 要求を処理が、場合でも、これらのサービスが、同じ AppDomain でホストされるは、ASP.NET のコンテンツに WCF サービスに送信される要求の処理に関与しません。 代わりに、WCF サービス モデルでは、WCF サービス宛てのメッセージをインターセプトし、それを WCF トランスポート/チャネル スタックを介してルーティングします。  
  
 この結果、サイド バイ サイド モデルは次のようになります。  
  
-   ASP.NET および WCF サービスは、AppDomain の状態を共有できます。 2 つのフレームワークは、同じ AppDomain で共存させることができます、ため WCF が ASP.NET (静的変数、イベントを含む) を使用した AppDomain の状態を共有できますも。  
  
-   WCF サービスのホスティング環境やトランスポートに依存しない、一貫した動作します。 ASP.NET HTTP ランタイムは意図的に、IIS/ASP.NET ホスティング環境や HTTP 通信と強く結合する形で設計されています。 WCF がホスティング環境間で一貫して動作するように設計されています逆に、(WCF には、一貫した動作両方の内部と IIS の外部) とトランスポートで (以降 IIS 7.0 でホストされているサービスが公開するすべてのエンドポイント間で一貫性のある動作を持つ場合でもそれらのエンドポイントのプロトコルを使用する HTTP 以外)。  
  
-   同じ AppDomain 内での HTTP ランタイムに実装された機能は、WCF ではなく、ASP.NET のコンテンツに適用されます。 ASP.NET アプリケーション プラットフォームの HTTP 固有の多くの機能は、ASP.NET のコンテンツを含む AppDomain 内でホストされる WCF サービスには適用されません。 このような機能の例を次に示します。  
  
    -   HttpContext:<xref:System.Web.HttpContext.Current%2A>は常に`null`WCF サービス内からアクセスする場合。 使用して<!--zz <xref:System.ServiceModel.OperationContext.Current.RequestContext>-->`RequestContext`代わりにします。  
  
    -   ファイル ベースの承認: サービス要求を承認するかどうかを決定するときに、サービスの .svc ファイルに適用されるアクセス制御リスト (ACL) の「WCF のセキュリティ モデルはできません。  
  
    -   構成ベースの URL 承認: 同様に、WCF のセキュリティ モデルに従っていない System.Web ので指定された URL ベースの承認ルール\<authorization > 構成要素。 これらの設定は、サービスは、ASP で保護された URL 空間に存在する場合、WCF 要求無視されます。NET の URL 承認規則。  
  
    -   HttpModule の拡張機能: WCF ホスティング インフラストラクチャは、WCF をインターセプト要求、<xref:System.Web.HttpApplication.PostAuthenticateRequest>イベントが生成され、ASP.NET HTTP パイプラインに処理は返しません。 パイプラインの後の段階で要求をインターセプトするように設計されたモジュールは、WCF 要求を途中受信できません。  
  
    -   ASP.NET の偽装: 既定では、WCF 要求常に実行するように IIS のプロセス id、System.Web を使用して偽装を有効にする ASP.NET が設定されている場合でも\<identity impersonate ="true"/> 構成オプション。  
  
 これらの制限は、IIS アプリケーションでホストされる WCF サービスにのみ適用されます。 ASP.NET のコンテンツの動作は、WCF の存在による影響はありません。  
  
 従来 HTTP パイプラインによって提供される機能を必要とする WCF アプリケーションでは、ホストは、トランスポートに依存しませんが、WCF 対応の使用を考慮してください。  
  
-   <xref:System.ServiceModel.OperationContext> (<xref:System.Web.HttpContext> の代わり)  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> (ASP.NET のファイル ベースまたは URL ベースの承認の代わり)  
  
-   <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> または独自の階層チャネル (HTTP モジュールの代わり)  
  
-   System.Web による偽装の代わりに WCF を使用して各操作の権限を借用します。  
  
 また、WCF の ASP.NET 互換モードで、サービスを実行しているを考慮することができます。  
  
## <a name="hosting-wcf-services-in-aspnet-compatibility-mode"></a>WCF サービスを ASP.NET 互換モードで提供する方法  
 WCF モデルは、ホスティング環境やトランスポート間で一貫して動作するよう設計されていますが、アプリケーションがこのレベルの柔軟性を必要としないシナリオは多くの場合があります。 WCF の ASP.NET 互換モードは、HTTP 以外のプロトコルで通信するために IIS の外部でホストする機能が不要なは、ASP.NET Web アプリケーション プラットフォームのすべての機能を使用する場合に適しています。  
  
 ここで、WCF ホスティング インフラストラクチャは、WCF メッセージを途中受信し、それをルーティングするには、HTTP パイプライン、既定のサイド バイ サイド構成とは異なり ASP.NET 互換モードで実行されている WCF サービスは ASP.NET の HTTP 要求のライフ サイクルで完全に参加します。 互換モードで WCF サービスはにより HTTP パイプラインを使用して、<xref:System.Web.IHttpHandler>実装では、ASPX ページや ASMX Web サービスの処理方法の要求に似ています。 その結果、WCF の動作と同じ ASMX 次の ASP.NET の機能に関して。  
  
-   <xref:System.Web.HttpContext>: ASP.NET 互換モードで実行されている WCF サービスがアクセスできる<xref:System.Web.HttpContext.Current%2A>および関連付けられた状態。  
  
-   ファイル ベースの承認: ASP.NET 互換モードで実行されている WCF サービスは、サービスの .svc ファイルをファイル システム アクセス制御リスト (Acl) をアタッチすることによりセキュリティで保護できます。  
  
-   URL 承認の設定: ASP です。NET の URL 承認規則は、WCF サービスが ASP.NET 互換モードで実行されている場合、WCF 要求に適用されます。  
  
-   <xref:System.Web.HttpModuleCollection> 機能拡張: ASP.NET 互換モードで実行するための WCF サービスは ASP.NET の HTTP 要求のライフ サイクルで完全に参加、HTTP パイプラインで構成されている任意の HTTP モジュールがサービスの呼び出しの前後に、WCF 要求を操作することです。  
  
-   ASP.NET の偽装: WCF サービス、ASP.NET の現在の id を使用して実行権限を借用スレッドで、アプリケーションの ASP.NET の偽装が有効になっている場合の IIS プロセス id と異なる場合があります。 ASP.NET の偽装と WCF の偽装は、両方が有効な場合、特定のサービス操作の最終的には、サービスの実装が WCF から取得した id を使用してを実行します。  
  
 WCF の ASP.NET 互換モードは、次の構成 (アプリケーションの Web.config ファイル内にある) を介して、アプリケーション レベルで有効です。  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />  
</system.serviceModel>  
```  
  
 既定値"`true`"を指定しない場合。 この値を設定"`false`"アプリケーションで実行されているすべての WCF サービスは ASP.NET 互換モードで実行していないことを示します。  
  
 ASP.NET 互換モードでは、基本的に、WCF の既定値から異なる要求の処理方法は、個々 のサービス実装であるために、制御できるように ASP.NET アプリケーション内で動作するかどうか互換性モードが有効になっています。 各サービスは、ASP.NET 互換モードをサポートするかどうかを、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> で示すことができます。 この属性の既定値は <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> です。  
  
 `[AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]`  
  
 `public class CalculatorService : ICalculatorSession`  
  
 `{//Implement calculator service methods.}`  
  
 アプリケーション全体を互換モードにしたとき、個々のサービスのサポート レベルがどうなるかを表に示します。  
  
|アプリケーション全体の互換モード設定|AspNetCompatibilityRequirementsMode <br /><br /> 設定|実際の動作|  
|--------------------------------------------------|---------------------------------------------------------|---------------------|  
|aspNetCompatibilityEnabled ="`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|サービスは正常に動作します。|  
|aspNetCompatibilityEnabled ="`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|サービスは正常に動作します。|  
|aspNetCompatibilityEnabled ="`true`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|サービスがメッセージを受信した時点でアクティベーション エラーが発生します。|  
|aspNetCompatibilityEnabled ="`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>|サービスがメッセージを受信した時点でアクティベーション エラーが発生します。|  
|aspNetCompatibilityEnabled ="`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>|サービスは正常に動作します。|  
|aspNetCompatibilityEnabled ="`false`"|<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.NotAllowed>|サービスは正常に動作します。|  
  
> [!NOTE]
>  IIS 7.0 や WAS は、HTTP 以外のプロトコル経由の通信を WCF サービスを使用します。 ただし、ASP.NET 互換モードを有効にするアプリケーションで実行されている WCF サービスは、非 HTTP エンドポイントを公開するは使用できません。 最初のメッセージを受信した時点で、アクティベーション例外が発生します。  
  
 WCF サービスの ASP.NET 互換モードを有効にする方法の詳細については、次を参照してください。<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode>と[ASP.NET との互換性](../../../../docs/framework/wcf/samples/aspnet-compatibility.md)サンプルです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>  
 [Windows Server App Fabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)
