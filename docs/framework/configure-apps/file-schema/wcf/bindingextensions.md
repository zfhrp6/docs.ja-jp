---
title: '&lt;bindingExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 02f29ec698584ebe8b2ca1b5d438ac06ba6503b5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltbindingextensionsgt"></a><span data-ttu-id="5bcb2-102">&lt;bindingExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="5bcb2-102">&lt;bindingExtensions&gt;</span></span>
<span data-ttu-id="5bcb2-103">このセクションは、コンピューターまたはアプリケーションの構成ファイルからユーザー定義のバインディングを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5bcb2-103">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="5bcb2-104">このコレクションにユーザー定義のバインディングを追加するには、`add` キーワードを使用し、要素の `type` 属性をユーザー定義のバインディングに設定して、`name` 属性をユーザー定義のバインディングの名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="5bcb2-104">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="5bcb2-105">バインディングの拡張により、ユーザーは、エンドポイント構成の一部として使用するユーザー定義のバインディングを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5bcb2-105">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="5bcb2-106">プログラムではバインディング拡張は、抽象クラス <xref:System.ServiceModel.Channels.Binding> を実装する型です。</span><span class="sxs-lookup"><span data-stu-id="5bcb2-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="5bcb2-107">次の例は、`add` 要素と `name` 属性を使用して、構成ファイルの `bindingElementExtensions` セクションにバインディング拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="5bcb2-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingExtensions>  
           <add name="MyBinding" type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="5bcb2-108">構成機能を要素に追加するには、ユーザーは `bindingSection` を記述して登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5bcb2-108">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="5bcb2-109">詳細については、<xref:System.Configuration> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bcb2-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="5bcb2-110">要素とその構成の型を定義したら、次の例に示すように拡張をエンドポイントの一部として使用できます。</span><span class="sxs-lookup"><span data-stu-id="5bcb2-110">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>  
    <service name="MyService">  
        <endpoint address="myAddress" binding="MyBinding" />  
    </service>  
</services>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5bcb2-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bcb2-111">See Also</span></span>  
 [<span data-ttu-id="5bcb2-112">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="5bcb2-112">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
