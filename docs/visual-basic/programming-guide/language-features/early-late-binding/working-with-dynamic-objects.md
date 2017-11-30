---
title: "動的オブジェクトの使用 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: da70c1e4c7398ad46d48c85b62ab884675bd1a73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="248fa-102">動的オブジェクトの使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="248fa-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="248fa-103">動的オブジェクト以外の別の方法を提供、`Object`実行時にオブジェクトへの遅延バインディングの種類。</span><span class="sxs-lookup"><span data-stu-id="248fa-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="248fa-104">動的オブジェクトで定義されている動的のインターフェイスを使用して実行時にプロパティとメソッドなどのメンバーを公開する、<xref:System.Dynamic>名前空間。</span><span class="sxs-lookup"><span data-stu-id="248fa-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="248fa-105">クラスを使用することができます、<xref:System.Dynamic>名前空間を静的な型または形式が一致しないデータ構造を操作するオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="248fa-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="248fa-106">IronPython および IronRuby などの動的な言語で定義されている動的オブジェクトを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="248fa-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="248fa-107">動的オブジェクトを作成したり、動的言語で定義されている動的オブジェクトを使用する方法を示す例については、次を参照してください。[チュートリアル: 動的オブジェクトの作成と使用](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、 <xref:System.Dynamic.DynamicObject>、または<xref:System.Dynamic.ExpandoObject>です。</span><span class="sxs-lookup"><span data-stu-id="248fa-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="248fa-108">使用して、動的言語ランタイムと IronPython および IronRuby などの動的言語から、オブジェクトにバインド、<xref:System.Dynamic.IDynamicMetaObjectProvider>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="248fa-108"> binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="248fa-109">実装するクラスの例については、`IDynamicMetaObjectProvider`のインターフェイスは、<xref:System.Dynamic.DynamicObject>と<xref:System.Dynamic.ExpandoObject>クラスです。</span><span class="sxs-lookup"><span data-stu-id="248fa-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="248fa-110">実装するオブジェクトを遅延バインディング呼び出しが行われたかどうか、`IDynamicMetaObjectProvider`インターフェイス、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]そのインターフェイスを使用して、オブジェクトを動的にオブジェクトにバインドします。</span><span class="sxs-lookup"><span data-stu-id="248fa-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="248fa-111">遅延バインディング呼び出しが実装されていないオブジェクトへ行われた場合、`IDynamicMetaObjectProvider`インターフェイス、またはへの呼び出し、`IDynamicMetaObjectProvider`インターフェイスの失敗した場合、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]の遅延バインディング機能を使用して、オブジェクトにバインド、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]ランタイム。</span><span class="sxs-lookup"><span data-stu-id="248fa-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] binds to the object by using the late-binding capabilities of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="248fa-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="248fa-112">See Also</span></span>  
 <xref:System.Dynamic.DynamicObject>  
 <xref:System.Dynamic.ExpandoObject>  
 [<span data-ttu-id="248fa-113">チュートリアル: 動的オブジェクトの作成と使用</span><span class="sxs-lookup"><span data-stu-id="248fa-113">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)  
 [<span data-ttu-id="248fa-114">事前バインディングと遅延バインディング</span><span class="sxs-lookup"><span data-stu-id="248fa-114">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
