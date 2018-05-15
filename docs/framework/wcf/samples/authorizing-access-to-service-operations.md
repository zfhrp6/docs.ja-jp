---
title: サービス操作へのアクセスの承認
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: b7f8b9b5fc4e6524da49b4d3f23de90a123e92e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="da819-102">サービス操作へのアクセスの承認</span><span class="sxs-lookup"><span data-stu-id="da819-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="da819-103">このサンプルを使用する方法を示します、 [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)の使用を有効にする、<xref:System.Security.Permissions.PrincipalPermissionAttribute>属性をサービス操作へのアクセスを承認します。</span><span class="sxs-lookup"><span data-stu-id="da819-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="da819-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="da819-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="da819-105">サービスとクライアントが構成を使用して、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="da819-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="da819-106">`mode`の属性、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)に設定されている`Message`と`clientCredentialType`に設定されている`Windows`です。</span><span class="sxs-lookup"><span data-stu-id="da819-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="da819-107"><xref:System.Security.Permissions.PrincipalPermissionAttribute> は各サービス メソッドに適用され、各操作へのアクセスを制限するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="da819-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="da819-108">呼び出し元は、各操作にアクセスできる Windows 管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="da819-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="da819-109">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="da819-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da819-110">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da819-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="da819-111">サービス構成ファイルを使用して、 [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)を設定する、`principalPermissionMode`属性。</span><span class="sxs-lookup"><span data-stu-id="da819-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>   
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="da819-112">`principalPermissionMode` を `UseWindowsGroups` に設定すると、Windows グループ名に基づいて <xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="da819-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="da819-113">呼び出し元が Windows 管理者グループのメンバーであることを要求するため、<xref:System.Security.Permissions.PrincipalPermissionAttribute> が各操作に適用されます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="da819-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```  
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="da819-114">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="da819-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="da819-115">クライアントが管理者グループのメンバーであるアカウントで実行される場合、クライアントは各操作と正常に通信できます。それ以外のアカウントで実行される場合、アクセスは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="da819-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="da819-116">承認エラーを試すには、管理グループのメンバーではないアカウントでクライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="da819-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="da819-117">クライアントをシャットダウンするには、コンソール ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="da819-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="da819-118"><xref:System.ServiceModel.Dispatcher.IErrorHandler> を実装すると、サービスに承認エラーを通知することができます。</span><span class="sxs-lookup"><span data-stu-id="da819-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="da819-119">参照してください[を拡張するコントロールをエラーの処理とレポート](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)実装する方法について`IErrorHandler`です。</span><span class="sxs-lookup"><span data-stu-id="da819-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="da819-120">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="da819-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="da819-121">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="da819-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="da819-122">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="da819-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="da819-123">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="da819-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da819-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="da819-124">See Also</span></span>
