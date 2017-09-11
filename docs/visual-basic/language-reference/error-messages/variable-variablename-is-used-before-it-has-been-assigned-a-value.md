---
title: "変数 &quot;&lt;variablename&gt;&quot; 値が割り当てられる前に使われる |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
dev_langs:
- VB
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
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
ms.openlocfilehash: dfc924ebbebb8b20654156b8871684dcfad6848a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="7edf5-102">変数 '&lt;variablename&gt;' 値が割り当てられる前に使われる</span><span class="sxs-lookup"><span data-stu-id="7edf5-102">Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value</span></span>
<span data-ttu-id="7edf5-103">変数 '\<variablename >' 値が割り当てられる前に使用します。</span><span class="sxs-lookup"><span data-stu-id="7edf5-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="7edf5-104">結果として、実行時に null 参照の例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7edf5-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="7edf5-105">アプリケーションには、少なくとも&1; つのパスをそのコードを任意の値が割り当てられる前に、変数を読み込むことがあります。</span><span class="sxs-lookup"><span data-stu-id="7edf5-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="7edf5-106">変数に値が割り当てられていない場合、変数はそのデータ型の既定値を保持します。</span><span class="sxs-lookup"><span data-stu-id="7edf5-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="7edf5-107">参照データ型では、その既定値は[Nothing](../../../visual-basic/language-reference/nothing.md)します。</span><span class="sxs-lookup"><span data-stu-id="7edf5-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="7edf5-108">値を持つ参照変数を読み取り`Nothing`が発生することができます、<xref:System.NullReferenceException>状況によって</xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="7edf5-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="7edf5-109">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="7edf5-109">By default, this message is a warning.</span></span> <span data-ttu-id="7edf5-110">警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。</span><span class="sxs-lookup"><span data-stu-id="7edf5-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="7edf5-111">**エラー ID:** bc42104 を生成します</span><span class="sxs-lookup"><span data-stu-id="7edf5-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7edf5-112">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="7edf5-112">To correct this error</span></span>  
  
-   <span data-ttu-id="7edf5-113">制御フローのロジックを確認し、変数が読み取られると、ステートメントに制御が渡される前に有効な値を持つかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="7edf5-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
-   <span data-ttu-id="7edf5-114">変数が常に有効な値を持つことを保証するために&1; つの方法では、その宣言の一部として初期化します。</span><span class="sxs-lookup"><span data-stu-id="7edf5-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="7edf5-115">「初期化」を参照してください[Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="7edf5-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7edf5-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7edf5-116">See Also</span></span>  
 <span data-ttu-id="7edf5-117">[Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7edf5-117">[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="7edf5-118"> [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="7edf5-118"> [Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="7edf5-119"> [変数のトラブルシューティング](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)</span><span class="sxs-lookup"><span data-stu-id="7edf5-119"> [Troubleshooting Variables](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)</span></span>
