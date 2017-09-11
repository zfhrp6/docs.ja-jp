---
title: "型の値 &quot;&lt;&quot; typename1 &quot;&gt;&quot;に変換できない&quot;&lt;typename2&gt;&quot; |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30955
- bc30955
dev_langs:
- VB
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
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
ms.openlocfilehash: 2fbe1550515d2b15a3e349392fc8d78812787ae4
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a><span data-ttu-id="5fb66-102">型の値 '&lt;' typename1 '&gt;'に変換できない'&lt;typename2&gt;'</span><span class="sxs-lookup"><span data-stu-id="5fb66-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="5fb66-103">型の値 '\<' typename1 '>' に変換できません。'\<typename2 >' です。</span><span class="sxs-lookup"><span data-stu-id="5fb66-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="5fb66-104">型の不一致ファイル参照アセンブリへのプロジェクト参照とを混在させるが考えられます '\<assemblyname >' です。</span><span class="sxs-lookup"><span data-stu-id="5fb66-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="5fb66-105">ファイルの参照を置き換えてください '\<filepath >' プロジェクトで'\<projectname1 >' への参照をプロジェクトに '\<projectname2 >' です。</span><span class="sxs-lookup"><span data-stu-id="5fb66-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="5fb66-106">プロジェクトがプロジェクト参照とファイル参照の両方を使用する場合、コンパイラは、別に、1 つの型を変換できることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="5fb66-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="5fb66-107">次の擬似コードは、このエラーを生成できる状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="5fb66-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 <span data-ttu-id="5fb66-108">プロジェクト`P1`プロジェクトを通じて間接的なプロジェクトで参照した`P2`プロジェクトに`P3`とへのファイルを直接参照も`P3`です。</span><span class="sxs-lookup"><span data-stu-id="5fb66-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="5fb66-109">宣言`commonObject`へのファイル参照を使用して`P3`への呼び出し中に`P2.getCommonClass`へのプロジェクト参照を使用して`P3`します。</span><span class="sxs-lookup"><span data-stu-id="5fb66-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="5fb66-110">この状況で問題は、ファイルのパスと名前の出力ファイルのファイル参照が指定される`P3`(通常 p3.dll) プロジェクト参照には、ソース プロジェクトが識別するときに (`P3`) プロジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="5fb66-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="5fb66-111">このため、コンパイラは保証できませんが、型`P3.commonClass`は&2; つの異なる参照を使用して、同じソース コードから取得します。</span><span class="sxs-lookup"><span data-stu-id="5fb66-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="5fb66-112">通常このような状況が発生したプロジェクト参照とファイル参照が混在します。</span><span class="sxs-lookup"><span data-stu-id="5fb66-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="5fb66-113">上の図で問題がない場合に発生する`P1`を直接プロジェクト参照した`P3`ファイル参照の代わりにします。</span><span class="sxs-lookup"><span data-stu-id="5fb66-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="5fb66-114">**エラー ID:** BC30955</span><span class="sxs-lookup"><span data-stu-id="5fb66-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5fb66-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="5fb66-115">To correct this error</span></span>  
  
-   <span data-ttu-id="5fb66-116">ファイルの参照をプロジェクト参照を変更します。</span><span class="sxs-lookup"><span data-stu-id="5fb66-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb66-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fb66-117">See Also</span></span>  
 <span data-ttu-id="5fb66-118">[Visual Basic における型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="5fb66-118">[Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="5fb66-119"> [プロジェクトの参照を管理します。](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="5fb66-119"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="5fb66-120"> [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span><span class="sxs-lookup"><span data-stu-id="5fb66-120"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span></span>
