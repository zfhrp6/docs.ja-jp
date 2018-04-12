---
title: 型 &#39;&lt;typename&gt;&#39; が定義されていません
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68eb37f43600c51dc9117c3785a12e3c8ede1965
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="3f393-102">型 &#39;&lt;typename&gt;&#39; が定義されていません</span><span class="sxs-lookup"><span data-stu-id="3f393-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="3f393-103">ステートメントには、定義されていない型への参照が行われます。</span><span class="sxs-lookup"><span data-stu-id="3f393-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="3f393-104">などの宣言ステートメントで型を定義できます`Enum`、 `Structure`、 `Class`、または`Interface`です。</span><span class="sxs-lookup"><span data-stu-id="3f393-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="3f393-105">**エラー ID:** BC30002</span><span class="sxs-lookup"><span data-stu-id="3f393-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3f393-106">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="3f393-106">To correct this error</span></span>  
  
-   <span data-ttu-id="3f393-107">型の定義とその参照の両方で同じスペル チェックを使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f393-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="3f393-108">型定義に、参照にアクセスできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f393-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="3f393-109">たとえば、型が別のモジュールでは、宣言されている場合`Private`、参照元のモジュール、型定義を移動または宣言`Public`です。</span><span class="sxs-lookup"><span data-stu-id="3f393-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="3f393-110">型の名前空間がプロジェクト内で再定義されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f393-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="3f393-111">場合を使用して、`Global`キーワード、型名を完全に修飾します。</span><span class="sxs-lookup"><span data-stu-id="3f393-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="3f393-112">たとえば、プロジェクトにという名前空間が定義されている場合`System`、<xref:System.Object?displayProperty=nameWithType>で完全修飾されている場合を除き、型にアクセスできません、`Global`キーワード:`Global.System.Object`です。</span><span class="sxs-lookup"><span data-stu-id="3f393-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="3f393-113">型が定義されている場合、オブジェクト ライブラリまたはが定義されているタイプ ライブラリに登録されていない場合[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]をクリックして**参照の追加**上、**プロジェクト**メニューのおよび適切なオブジェクトを選択ライブラリまたはタイプ ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="3f393-113">If the type is defined, but the object library or type library in which it is defined is not registered in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="3f393-114">種類が対象となる .NET Framework プロファイルの一部であるアセンブリ内であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f393-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="3f393-115">詳細については、「[.NET Framework を対象とするエラーのトラブルシューティング](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f393-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f393-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f393-116">See Also</span></span>  
 [<span data-ttu-id="3f393-117">Visual Basic における名前空間</span><span class="sxs-lookup"><span data-stu-id="3f393-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="3f393-118">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="3f393-118">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="3f393-119">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="3f393-119">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="3f393-120">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="3f393-120">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="3f393-121">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="3f393-121">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="3f393-122">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="3f393-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
