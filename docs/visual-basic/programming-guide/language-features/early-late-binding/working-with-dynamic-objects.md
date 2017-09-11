---
title: "動的オブジェクト (Visual Basic) の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d1e1c4f7338daad0f1101f6e886eba6c37316b0e
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="working-with-dynamic-objects-visual-basic"></a><span data-ttu-id="981e1-102">動的オブジェクトの使用 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="981e1-102">Working with Dynamic Objects (Visual Basic)</span></span>
<span data-ttu-id="981e1-103">動的オブジェクトの他にも、別の方法を提供、`Object`実行時にオブジェクトに遅延バインディングの種類。</span><span class="sxs-lookup"><span data-stu-id="981e1-103">Dynamic objects provide another way, other than the `Object` type, to late bind to an object at run time.</span></span> <span data-ttu-id="981e1-104">動的オブジェクトで定義されている動的インターフェイスを使用して実行時にプロパティとメソッドのなどのメンバーを公開する、<xref:System.Dynamic>名前空間</xref:System.Dynamic>。</span><span class="sxs-lookup"><span data-stu-id="981e1-104">A dynamic object exposes members such as properties and methods at run time by using dynamic interfaces that are defined in the <xref:System.Dynamic> namespace.</span></span> <span data-ttu-id="981e1-105">内のクラスを使用する、<xref:System.Dynamic>名前空間を静的な型または形式が一致しないデータ構造を操作するオブジェクトを作成します</xref:System.Dynamic>。</span><span class="sxs-lookup"><span data-stu-id="981e1-105">You can use the classes in the <xref:System.Dynamic> namespace to create objects that work with data structures that do not match a static type or format.</span></span> <span data-ttu-id="981e1-106">IronPython および IronRuby などの動的言語で定義されている動的オブジェクトを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="981e1-106">You can also use the dynamic objects that are defined in dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="981e1-107">動的オブジェクトを作成したり、動的言語で定義されている動的オブジェクトを使用する方法を示す例については、次を参照してください[チュートリアル: 動的オブジェクトの作成および使用して](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)、 <xref:System.Dynamic.DynamicObject>、または<xref:System.Dynamic.ExpandoObject>.</xref:System.Dynamic.ExpandoObject> </xref:System.Dynamic.DynamicObject> 。</span><span class="sxs-lookup"><span data-stu-id="981e1-107">For examples that show how to create dynamic objects or use a dynamic object defined in a dynamic language, see [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>, or <xref:System.Dynamic.ExpandoObject>.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="981e1-108">使用して、動的言語ランタイムと IronPython および IronRuby などの動的言語のオブジェクトにバインド、<xref:System.Dynamic.IDynamicMetaObjectProvider>インターフェイス</xref:System.Dynamic.IDynamicMetaObjectProvider>。</span><span class="sxs-lookup"><span data-stu-id="981e1-108"> binds to objects from the dynamic language runtime and dynamic languages such as IronPython and IronRuby by using the <xref:System.Dynamic.IDynamicMetaObjectProvider> interface.</span></span> <span data-ttu-id="981e1-109">実装するクラスの例として、`IDynamicMetaObjectProvider`インターフェイスは、<xref:System.Dynamic.DynamicObject>と<xref:System.Dynamic.ExpandoObject>クラス</xref:System.Dynamic.ExpandoObject></xref:System.Dynamic.DynamicObject>。</span><span class="sxs-lookup"><span data-stu-id="981e1-109">Examples of classes that implement the `IDynamicMetaObjectProvider` interface are the <xref:System.Dynamic.DynamicObject> and <xref:System.Dynamic.ExpandoObject> classes.</span></span>  
  
 <span data-ttu-id="981e1-110">実装するオブジェクトに遅延バインディング呼び出しを行ったかどうか、`IDynamicMetaObjectProvider`インターフェイス、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]そのインターフェイスを使用して、オブジェクトを動的にオブジェクトにバインドします。</span><span class="sxs-lookup"><span data-stu-id="981e1-110">If a late-bound call is made to an object that implements the `IDynamicMetaObjectProvider` interface, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] binds to the dynamic object by using that interface.</span></span> <span data-ttu-id="981e1-111">遅延バインディング呼び出しが実装されていないオブジェクトに加えられた場合、`IDynamicMetaObjectProvider`インターフェイス、またはへの呼び出し、`IDynamicMetaObjectProvider`インターフェイスの失敗した場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]オブジェクトの遅延バインディングの機能を使用して、バインド、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ランタイム。</span><span class="sxs-lookup"><span data-stu-id="981e1-111">If a late-bound call is made to an object that does not implement the `IDynamicMetaObjectProvider` interface, or if the call to the `IDynamicMetaObjectProvider` interface fails, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] binds to the object by using the late-binding capabilities of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="981e1-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="981e1-112">See Also</span></span>  
 <span data-ttu-id="981e1-113"><xref:System.Dynamic.DynamicObject></xref:System.Dynamic.DynamicObject></span><span class="sxs-lookup"><span data-stu-id="981e1-113"><xref:System.Dynamic.DynamicObject></span></span>   
 <span data-ttu-id="981e1-114"><xref:System.Dynamic.ExpandoObject></xref:System.Dynamic.ExpandoObject></span><span class="sxs-lookup"><span data-stu-id="981e1-114"><xref:System.Dynamic.ExpandoObject></span></span>   
<span data-ttu-id="981e1-115"> [チュートリアル: 作成と動的オブジェクトの使用](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md) </span><span class="sxs-lookup"><span data-stu-id="981e1-115"> [Walkthrough: Creating and Using Dynamic Objects](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md) </span></span>  
<span data-ttu-id="981e1-116"> [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span><span class="sxs-lookup"><span data-stu-id="981e1-116"> [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)</span></span>
