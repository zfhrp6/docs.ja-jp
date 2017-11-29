---
title: '&lt;bindingElementExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b12752980e43944bb73f8adfde04bfb2d4dadf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindingelementextensionsgt"></a><span data-ttu-id="2fc60-102">&lt;bindingElementExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="2fc60-102">&lt;bindingElementExtensions&gt;</span></span>
<span data-ttu-id="2fc60-103">このセクションは、コンピューターまたはアプリケーションの構成ファイルからカスタム バインド要素を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2fc60-103">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="2fc60-104">このコレクションにカスタム バインディング要素を追加するには、`add` キーワードを使用し、要素の `type` 属性をバインディング要素拡張に設定して、`name` 属性をカスタム バインディング要素に設定します。</span><span class="sxs-lookup"><span data-stu-id="2fc60-104">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="2fc60-105">バインディングの拡張により、ユーザーは、カスタム バインディングの一部として使用するユーザー定義のバインディング要素を作成できます。</span><span class="sxs-lookup"><span data-stu-id="2fc60-105">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="2fc60-106">プログラムではバインディング拡張は、抽象クラス <xref:System.ServiceModel.Channels.BindingElement> を実装する型です。</span><span class="sxs-lookup"><span data-stu-id="2fc60-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="2fc60-107">構成ファイルでは、`bindingElementExtensions` セクションは、拡張要素を定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2fc60-107">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="2fc60-108">次の例は、`add` 要素と `name` 属性を使用して、構成ファイルの `bindingElementExtensions` セクションにバインディング拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="2fc60-108">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="2fc60-109">構成機能を要素に追加するには、ユーザーは `bindingElementExtensionSection` を記述して登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fc60-109">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="2fc60-110">詳細については、<xref:System.Configuration> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fc60-110">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="2fc60-111">要素とその構成の型を定義したら、次の例に示すように拡張をカスタム バインディングの一部として使用できます。</span><span class="sxs-lookup"><span data-stu-id="2fc60-111">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2fc60-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="2fc60-112">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>  
 [<span data-ttu-id="2fc60-113">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="2fc60-113">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
