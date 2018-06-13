---
title: WCF サービス パフォーマンスを制御するための ServiceThrottlingBehavior の使用
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: b54d1d6146b9751fdd12502771de01fe52854c07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498050"
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a><span data-ttu-id="3441f-102">WCF サービス パフォーマンスを制御するための ServiceThrottlingBehavior の使用</span><span class="sxs-lookup"><span data-stu-id="3441f-102">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>
<span data-ttu-id="3441f-103"><xref:System.ServiceModel.Description.ServiceThrottlingBehavior> クラスでは、アプリケーション レベルで作成されるインスタンス数またはセッション数の制限に使用できるプロパティが公開されています。</span><span class="sxs-lookup"><span data-stu-id="3441f-103">The <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class exposes properties that you can use to limit how many instances or sessions are created at the application level.</span></span> <span data-ttu-id="3441f-104">この動作を使用して、Windows Communication Foundation (WCF) アプリケーションのパフォーマンスを微調整できます。</span><span class="sxs-lookup"><span data-stu-id="3441f-104">Using this behavior, you can fine-tune the performance of your Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a><span data-ttu-id="3441f-105">サービス インスタンスと同時呼び出しの制御</span><span class="sxs-lookup"><span data-stu-id="3441f-105">Controlling Service Instances and Concurrent Calls</span></span>  
 <span data-ttu-id="3441f-106"><xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> プロパティを使用して、<xref:System.ServiceModel.ServiceHost> クラスでアクティブに処理されるメッセージの最大数を指定します。また、<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> プロパティを使用して、サービス内の <xref:System.ServiceModel.InstanceContext> オブジェクトの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="3441f-106">Use the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> property to specify the maximum number of messages actively processing across a <xref:System.ServiceModel.ServiceHost> class, and the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> property to specify the maximum number of <xref:System.ServiceModel.InstanceContext> objects in the service.</span></span>  
  
 <span data-ttu-id="3441f-107">これらのプロパティの設定を確認して通常は実際の動作に対するアプリケーションの実行後に行われるのための設定を読み込みます、<xref:System.ServiceModel.Description.ServiceThrottlingBehavior>プロパティは、通常、アプリケーション構成ファイルを使用して指定します[ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)要素。</span><span class="sxs-lookup"><span data-stu-id="3441f-107">Because determining the settings for these properties usually takes place after real-world experience running the application against loads, the settings for the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> properties is typically specified in an application configuration file using the [\<serviceThrottling>](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) element.</span></span>  
  
 <span data-ttu-id="3441f-108">簡単な例として、<xref:System.ServiceModel.Description.ServiceThrottlingBehavior>、<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>、および <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> の各プロパティを 1 に設定するアプリケーション構成ファイルから <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> クラスを使用する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="3441f-108">The following code example shows the use of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class from an application configuration file that sets the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> properties to 1 as a trivial example.</span></span> <span data-ttu-id="3441f-109">特定のアプリケーションでの最適な設定については、実際の動作から判断します。</span><span class="sxs-lookup"><span data-stu-id="3441f-109">Real-world experience determines the optimal settings for any particular application.</span></span>  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 <span data-ttu-id="3441f-110">実行時における正確な動作は <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> プロパティと <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティの値により異なります。この値により、操作内で一度に実行できるメッセージ数や、受信チャネル セッションに関連するサービス <xref:System.ServiceModel.InstanceContext> の有効期間をそれぞれ制限します。</span><span class="sxs-lookup"><span data-stu-id="3441f-110">The exact run-time behavior depends upon the values of the <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> and <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> properties, which control how many messages can execute inside an operation at once and the lifetimes of the service <xref:System.ServiceModel.InstanceContext> relative to incoming channel sessions, respectively.</span></span>  
  
 <span data-ttu-id="3441f-111">詳細については、「<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>」および「<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3441f-111">For details, see <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3441f-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="3441f-112">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
