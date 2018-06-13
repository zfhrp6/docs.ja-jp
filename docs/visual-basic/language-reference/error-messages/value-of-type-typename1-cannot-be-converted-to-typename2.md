---
title: 型の値&#39; &lt;typename1&gt; &#39;に変換できない&#39; &lt;typename2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 9b3c029ed7bf73ff92dba65438d797b27fa135f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595239"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a><span data-ttu-id="6b5bd-102">型の値&#39; &lt;typename1&gt; &#39;に変換できない&#39; &lt;typename2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="6b5bd-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="6b5bd-103">型の値 '\<typename1 >' に変換できません。'\<typename2 >' です。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="6b5bd-104">型の不一致は、ファイル参照アセンブリへの参照をプロジェクトとの混合によって生じた可能性があります '\<assemblyname >' です。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-104">Type mismatch could be due to the mixing of a file reference with a project reference to assembly '\<assemblyname>'.</span></span> <span data-ttu-id="6b5bd-105">ファイル参照を置き換えてください '\<filepath >' プロジェクトで'\<projectname1 >' への参照をプロジェクトに '\<projectname2 >' です。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-105">Try replacing the file reference to '\<filepath>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="6b5bd-106">プロジェクトがプロジェクト参照とファイル参照の両方を使用する場合、コンパイラは、別に、1 つの型を変換できることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-106">In a situation where a project makes both a project reference and a file reference, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="6b5bd-107">次の擬似コードは、このエラーを生成できる状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-107">The following pseudo-code illustrates a situation that can generate this error.</span></span>  
  
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
  
 <span data-ttu-id="6b5bd-108">プロジェクト`P1`プロジェクト全体の間接的なプロジェクト参照は、`P2`プロジェクトに`P3`とへのファイルを直接参照も`P3`します。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-108">Project `P1` makes an indirect project reference through project `P2` to project `P3`, and also a direct file reference to `P3`.</span></span> <span data-ttu-id="6b5bd-109">宣言`commonObject`へのファイル参照を使用して`P3`への呼び出し中に`P2.getCommonClass`へのプロジェクト参照を使用して`P3`です。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-109">The declaration of `commonObject` uses the file reference to `P3`, while the call to `P2.getCommonClass` uses the project reference to `P3`.</span></span>  
  
 <span data-ttu-id="6b5bd-110">このような状況に問題は、ファイルのパスと名前の出力ファイルのファイル参照が指定される`P3`(通常 p3.dll) プロジェクト参照には、ソース プロジェクトが識別するときに (`P3`) プロジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-110">The problem in this situation is that the file reference specifies a file path and name for the output file of `P3` (typically p3.dll), while the project references identify the source project (`P3`) by project name.</span></span> <span data-ttu-id="6b5bd-111">このため、コンパイラは保証できませんを種類`P3.commonClass`は 2 つの異なる参照を使用して、同じソース コードから取得します。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-111">Because of this, the compiler cannot guarantee that the type `P3.commonClass` comes from the same source code through the two different references.</span></span>  
  
 <span data-ttu-id="6b5bd-112">通常このような状況が発生したときにプロジェクト参照とファイル参照が混在します。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-112">This situation typically occurs when project references and file references are mixed.</span></span> <span data-ttu-id="6b5bd-113">前の図では、問題がない場合に発生する`P1`を直接プロジェクト参照した`P3`ファイル参照の代わりにします。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-113">In the preceding illustration, the problem would not occur if `P1` made a direct project reference to `P3` instead of a file reference.</span></span>  
  
 <span data-ttu-id="6b5bd-114">**エラー ID:** BC30955</span><span class="sxs-lookup"><span data-stu-id="6b5bd-114">**Error ID:** BC30955</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6b5bd-115">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6b5bd-115">To correct this error</span></span>  
  
-   <span data-ttu-id="6b5bd-116">ファイル参照をプロジェクト参照を変更します。</span><span class="sxs-lookup"><span data-stu-id="6b5bd-116">Change the file reference to a project reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b5bd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b5bd-117">See Also</span></span>  
 [<span data-ttu-id="6b5bd-118">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="6b5bd-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="6b5bd-119">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="6b5bd-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 
