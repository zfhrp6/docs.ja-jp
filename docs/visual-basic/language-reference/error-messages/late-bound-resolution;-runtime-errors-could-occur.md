---
title: "遅延バインディングの解決実行時エラーが発生する可能性があります。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
dev_langs:
- VB
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
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
ms.openlocfilehash: 3baf28a17077d255b42f38ade21ce6153c24e862
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="bc7d3-102">遅延バインドの解決です。ランタイム エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bc7d3-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="bc7d3-103">として宣言された変数にオブジェクトが割り当てられている、 [Object データ型](../../../visual-basic/language-reference/data-types/object-data-type.md)します。</span><span class="sxs-lookup"><span data-stu-id="bc7d3-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="bc7d3-104">として変数を宣言すると`Object`、コンパイラを実行する必要があります*遅延バインディング*、これにより実行時に余分な処理が発生します。</span><span class="sxs-lookup"><span data-stu-id="bc7d3-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="bc7d3-105">また、アプリケーションで実行時エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bc7d3-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="bc7d3-106">割り当てる場合など、<xref:System.Windows.Forms.Form>に、`Object`変数にアクセスしようと、<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName>プロパティには、ランタイムは、スロー、<xref:System.MemberAccessException>ため、<xref:System.Windows.Forms.Form>クラスを公開しません、`NameTable`プロパティ</xref:System.Windows.Forms.Form></xref:System.MemberAccessException></xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName></xref:System.Windows.Forms.Form>。</span><span class="sxs-lookup"><span data-stu-id="bc7d3-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="bc7d3-107">特定の種類を指定して変数を宣言する場合、コンパイラを実行できます*事前バインディング*コンパイル時にします。</span><span class="sxs-lookup"><span data-stu-id="bc7d3-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="bc7d3-108">これは、結果、パフォーマンスの向上、制御されたアクセスを特定の型のメンバーと、コードの読みやすさをします。</span><span class="sxs-lookup"><span data-stu-id="bc7d3-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="bc7d3-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="bc7d3-109">By default, this message is a warning.</span></span> <span data-ttu-id="bc7d3-110">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bc7d3-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="bc7d3-111">**エラー ID:** BC42017</span><span class="sxs-lookup"><span data-stu-id="bc7d3-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bc7d3-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="bc7d3-112">To correct this error</span></span>  
  
-   <span data-ttu-id="bc7d3-113">可能であれば、特定の種類を指定して変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="bc7d3-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc7d3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc7d3-114">See Also</span></span>  
 <span data-ttu-id="bc7d3-115">[事前バインディングと遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span><span class="sxs-lookup"><span data-stu-id="bc7d3-115">[Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span></span>  
<span data-ttu-id="bc7d3-116"> [オブジェクト変数の宣言](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)</span><span class="sxs-lookup"><span data-stu-id="bc7d3-116"> [Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)</span></span>
