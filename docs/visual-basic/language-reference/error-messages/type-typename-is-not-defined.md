---
title: "型 &quot;&lt;typename&gt;&quot; が定義されていない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
dev_langs:
- VB
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
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
ms.openlocfilehash: 55b76e9d080a2e2e9fe6e9737a713524ea6409f6
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="e0d0f-102">型 '&lt;typename&gt;' が定義されていません</span><span class="sxs-lookup"><span data-stu-id="e0d0f-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="e0d0f-103">ステートメントでは、定義されていない型への参照をしました。</span><span class="sxs-lookup"><span data-stu-id="e0d0f-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="e0d0f-104">などの宣言ステートメントで型を定義できる`Enum`、 `Structure`、 `Class`、または`Interface`です。</span><span class="sxs-lookup"><span data-stu-id="e0d0f-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="e0d0f-105">**エラー ID:** BC30002</span><span class="sxs-lookup"><span data-stu-id="e0d0f-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e0d0f-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="e0d0f-106">To correct this error</span></span>  
  
-   <span data-ttu-id="e0d0f-107">型の定義とその参照の両方で同じスペル チェックを使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e0d0f-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="e0d0f-108">型の定義が参照にアクセスできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e0d0f-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="e0d0f-109">たとえば、型が別のモジュールでは、宣言されている場合`Private`を参照しているモジュールに、型定義を移行または宣言`Public`します。</span><span class="sxs-lookup"><span data-stu-id="e0d0f-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="e0d0f-110">型の名前空間がプロジェクト内で再定義されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="e0d0f-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="e0d0f-111">使用している場合、`Global`完全型名を修飾するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="e0d0f-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="e0d0f-112">たとえば、プロジェクトに名前空間が定義されている場合`System`、<xref:System.Object?displayProperty=fullName>で完全修飾されている場合を除き、型にアクセスできません、`Global`キーワード: `Global.System.Object`</xref:System.Object?displayProperty=fullName> 。</span><span class="sxs-lookup"><span data-stu-id="e0d0f-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=fullName> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="e0d0f-113">型を定義するとしても、オブジェクト ライブラリまたはが定義されているタイプ ライブラリに登録されていない[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、 をクリックして**参照の追加**上、**プロジェクト**] メニューの [し適切なオブジェクト ライブラリまたはタイプ ライブラリを選択します。</span><span class="sxs-lookup"><span data-stu-id="e0d0f-113">If the type is defined, but the object library or type library in which it is defined is not registered in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="e0d0f-114">対象となる .NET Framework プロファイルの一部であるアセンブリで型があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e0d0f-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="e0d0f-115">詳細については、次を参照してください。 [.NET Framework を対象とするエラーのトラブルシューティング](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)します。</span><span class="sxs-lookup"><span data-stu-id="e0d0f-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0d0f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0d0f-116">See Also</span></span>  
 <span data-ttu-id="e0d0f-117">[Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="e0d0f-117">[Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="e0d0f-118"> [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e0d0f-118"> [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) </span></span>  
<span data-ttu-id="e0d0f-119"> [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e0d0f-119"> [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="e0d0f-120"> [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e0d0f-120"> [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) </span></span>  
<span data-ttu-id="e0d0f-121"> [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e0d0f-121"> [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="e0d0f-122"> [プロジェクト内の参照の管理](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)</span><span class="sxs-lookup"><span data-stu-id="e0d0f-122"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)</span></span>
