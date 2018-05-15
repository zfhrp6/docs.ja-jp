---
title: '&lt;bindingElementExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: a93474a4f86fac2a6b211652e3ddc86901cf197f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltbindingelementextensionsgt"></a><span data-ttu-id="bf750-102">&lt;bindingElementExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="bf750-102">&lt;bindingElementExtensions&gt;</span></span>
<span data-ttu-id="bf750-103">このセクションは、コンピューターまたはアプリケーションの構成ファイルからカスタム バインド要素を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf750-103">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="bf750-104">このコレクションにカスタム バインディング要素を追加するには、`add` キーワードを使用し、要素の `type` 属性をバインディング要素拡張に設定して、`name` 属性をカスタム バインディング要素に設定します。</span><span class="sxs-lookup"><span data-stu-id="bf750-104">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="bf750-105">バインディングの拡張により、ユーザーは、カスタム バインディングの一部として使用するユーザー定義のバインディング要素を作成できます。</span><span class="sxs-lookup"><span data-stu-id="bf750-105">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="bf750-106">プログラムではバインディング拡張は、抽象クラス <xref:System.ServiceModel.Channels.BindingElement> を実装する型です。</span><span class="sxs-lookup"><span data-stu-id="bf750-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="bf750-107">構成ファイルでは、`bindingElementExtensions` セクションは、拡張要素を定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bf750-107">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="bf750-108">次の例は、`add` 要素と `name` 属性を使用して、構成ファイルの `bindingElementExtensions` セクションにバインディング拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="bf750-108">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingElementExtensions>  
           <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingElementExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="bf750-109">構成機能を要素に追加するには、ユーザーは `bindingElementExtensionSection` を記述して登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf750-109">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="bf750-110">詳細については、<xref:System.Configuration> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf750-110">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="bf750-111">要素とその構成の型を定義したら、次の例に示すように拡張をカスタム バインドの一部として使用できます。</span><span class="sxs-lookup"><span data-stu-id="bf750-111">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf750-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf750-112">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>  
 [<span data-ttu-id="bf750-113">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="bf750-113">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
