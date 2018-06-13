---
title: '&lt;comContracts&gt;'
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: b44c09e7e32129ba21834f7fbb8dc4699904e46b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746411"
---
# <a name="ltcomcontractsgt"></a><span data-ttu-id="49e2d-102">&lt;comContracts&gt;</span><span class="sxs-lookup"><span data-stu-id="49e2d-102">&lt;comContracts&gt;</span></span>
<span data-ttu-id="49e2d-103">`comContracts` 構成セクションには、COM+ 統合サービス コントラクトのさまざまなプロパティを指定できる要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="49e2d-103">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="49e2d-104">名前空間およびコントラクトの指定</span><span class="sxs-lookup"><span data-stu-id="49e2d-104">Specifying Namespace and Contract</span></span>  
 <span data-ttu-id="49e2d-105">COM + 統合サービス コントラクトは現在に制限されて、"http://tempuri.org"名前空間、およびコントラクト名がサポートする COM インターフェイスから派生します。</span><span class="sxs-lookup"><span data-stu-id="49e2d-105">COM+ integration service contracts are currently restricted to the "http://tempuri.org" namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="49e2d-106">ただし、構成ファイルの `comContracts` セクションを使用して候補を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="49e2d-106">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="49e2d-107">たとえば、次の構成を使用して、サービス コントラクトの名前空間とコントラクト名、およびセッションの多いバインディングで使用させるオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="49e2d-107">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
  </comContract>  
</comContracts>  
```  
  
 <span data-ttu-id="49e2d-108">サービスが初期化される場合、指定した名前空間およびコントラクト名が、生成されるサービスの説明に適用されます。</span><span class="sxs-lookup"><span data-stu-id="49e2d-108">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="49e2d-109">このセクションが空の場合、サービスの初期化によって、サポートしている COM インターフェイス ID から取得された既定の名前空間およびコントラクト名が適用されます。</span><span class="sxs-lookup"><span data-stu-id="49e2d-109">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="49e2d-110">さらに、使用することができます、 [ \<exposedMethod >](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) COM + コンポーネントのインターフェイスが Web サービスとして公開されるときに公開される COM + メソッドを指定する要素。</span><span class="sxs-lookup"><span data-stu-id="49e2d-110">In addition, you can use the [\<exposedMethod>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="49e2d-111">使用することも、 [ \<persistableTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)統合で使用される永続化できる型を指定します。</span><span class="sxs-lookup"><span data-stu-id="49e2d-111">You can also use the [\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="49e2d-112">最後に、使用することができます、 [ \<userDefinedType >](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)に含めるユーザー定義型 (UDT) をサービス コントラクトに含まれる要素です。</span><span class="sxs-lookup"><span data-stu-id="49e2d-112">Finally, you can use the [\<userDefinedType>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49e2d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="49e2d-113">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComContractElementCollection>  
 <xref:System.ServiceModel.Configuration.ComContractElement>  
 [<span data-ttu-id="49e2d-114">\<exposedMethod></span><span class="sxs-lookup"><span data-stu-id="49e2d-114">\<exposedMethod></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/exposedmethod.md)  
 [<span data-ttu-id="49e2d-115">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="49e2d-115">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)  
 [<span data-ttu-id="49e2d-116">\<userDefinedType></span><span class="sxs-lookup"><span data-stu-id="49e2d-116">\<userDefinedType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/userdefinedtype.md)  
 [<span data-ttu-id="49e2d-117">\<comContract></span><span class="sxs-lookup"><span data-stu-id="49e2d-117">\<comContract></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontract.md)  
 [<span data-ttu-id="49e2d-118">COM+ アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="49e2d-118">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="49e2d-119">方法 : COM+ サービス設定を構成する</span><span class="sxs-lookup"><span data-stu-id="49e2d-119">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
