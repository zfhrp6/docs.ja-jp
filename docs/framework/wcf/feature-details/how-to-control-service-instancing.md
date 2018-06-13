---
title: '方法 : サービスのインスタンス化を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 2f9e4f298eb95498ec8d3603624763bfd95bfda1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489145"
---
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="4dac2-102">方法 : サービスのインスタンス化を制御する</span><span class="sxs-lookup"><span data-stu-id="4dac2-102">How to: Control Service Instancing</span></span>
<span data-ttu-id="4dac2-103">サービスのインスタンス モードを設定することにより、<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (およびそのユーザー定義のサービス オブジェクト) をいつ生成するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4dac2-103">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="4dac2-104">設定できるモードについては、<xref:System.ServiceModel.InstanceContextMode> 列挙体を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dac2-104">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> <span data-ttu-id="4dac2-105">動作に関する詳細については、次を参照してください。[を構成すると、ランタイムのビヘイビアーの使用を拡張する](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)です。</span><span class="sxs-lookup"><span data-stu-id="4dac2-105">For more information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="4dac2-106">実施例については、次を参照してください。[動作](../../../../docs/framework/wcf/samples/behaviors.md)です。</span><span class="sxs-lookup"><span data-stu-id="4dac2-106">For working examples, see [Behaviors](../../../../docs/framework/wcf/samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="4dac2-107">サービス インスタンスの有効期間をコードで制御するには</span><span class="sxs-lookup"><span data-stu-id="4dac2-107">To control the service instance lifetime using code</span></span>  
  
1.  <span data-ttu-id="4dac2-108">サービス クラスに <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="4dac2-108">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2.  <span data-ttu-id="4dac2-109"><xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティを <xref:System.ServiceModel.InstanceContextMode.PerCall>、<xref:System.ServiceModel.InstanceContextMode.PerSession>、<xref:System.ServiceModel.InstanceContextMode.Single> のいずれかの値に設定します。</span><span class="sxs-lookup"><span data-stu-id="4dac2-109">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="4dac2-110">例</span><span class="sxs-lookup"><span data-stu-id="4dac2-110">Example</span></span>  
 <span data-ttu-id="4dac2-111"><xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 属性の <xref:System.ServiceModel.ServiceBehaviorAttribute> プロパティを <xref:System.ServiceModel.InstanceContextMode.PerCall> に設定するコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="4dac2-111">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4dac2-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="4dac2-112">See Also</span></span>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>  
 <xref:System.ServiceModel.InstanceContextMode>  
 [<span data-ttu-id="4dac2-113">サービス: 動作のサンプル</span><span class="sxs-lookup"><span data-stu-id="4dac2-113">Service: Behaviors Samples</span></span>](http://msdn.microsoft.com/library/4e3c6513-a7ff-4b35-8dcf-b5506c6f39a7)
