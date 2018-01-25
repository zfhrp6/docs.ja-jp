---
title: "-checked (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c0a8cc66609fe542fc7db166cd208cfcedb204b8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="4dd1c-102">-checked (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="4dd1c-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="4dd1c-103">**-checked** オプションは、データ型の範囲外の値になる整数の算術ステートメントと、[checked](../../../csharp/language-reference/keywords/checked.md) または [unchecked](../../../csharp/language-reference/keywords/unchecked.md) キーワードのスコープ内に含まれない整数の算術ステートメントで、ランタイム例外が発生するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../../../csharp/language-reference/keywords/checked.md) or [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dd1c-104">構文</span><span class="sxs-lookup"><span data-stu-id="4dd1c-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="4dd1c-105">コメント</span><span class="sxs-lookup"><span data-stu-id="4dd1c-105">Remarks</span></span>  
 <span data-ttu-id="4dd1c-106">`checked` または `unchecked` キーワードのスコープ内に含まれる整数の算術ステートメントは、**-checked** オプションの作用の対象になりません。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="4dd1c-107">`checked` または `unchecked` キーワードのスコープ内に含まれない整数の算術ステートメントがデータ型の範囲外の値になり、**-checked+** (**-checked**) がコンパイル時に使用されている場合は、そのステートメントでランタイム例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (**-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="4dd1c-108">**-checked-** がコンパイル時に使用された場合、そのステートメントでランタイム例外は発生しません。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="4dd1c-109">このオプションの既定値は **-checked-** です。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-109">The default value for this option is **-checked-**.</span></span> <span data-ttu-id="4dd1c-110">**-checked-** を使用する 1 つのシナリオとして、大規模なアプリケーションをビルドする場合があります。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-110">One scenario for using **-checked-** is in building large applications.</span></span> <span data-ttu-id="4dd1c-111">場合によって、このようなアプリケーションのビルドには自動化ツールが使用されます。そのようなツールで **-checked** が自動的に + に設定されることがあります。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-111">Sometimes automated tools are used to build such applications, and such a tool might automatically set **-checked** to +.</span></span> <span data-ttu-id="4dd1c-112">**-checked-** を指定することにより、ツールのグローバルな既定値を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-112">You can override the tool's global default by specifying **-checked-**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4dd1c-113">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="4dd1c-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="4dd1c-114">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="4dd1c-115">詳細については、「[Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)」([ビルド] ページ (プロジェクト デザイナー) (C#)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="4dd1c-116">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="4dd1c-117">**[詳細設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="4dd1c-118">**[演算のオーバーフローおよびアンダーフローのチェック]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-118">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="4dd1c-119">プログラムによってこのコンパイラ オプションにアクセスする方法については、<xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A> に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dd1c-120">例</span><span class="sxs-lookup"><span data-stu-id="4dd1c-120">Example</span></span>  
 <span data-ttu-id="4dd1c-121">次のコマンドは `t2.cs` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="4dd1c-122">コマンドで使用されている `-checked` は、ファイル内の整数の算術ステートメントのうち、`checked` または `unchecked` キーワードのスコープ内に含まれず、データ型の範囲外の値になるステートメントで、ランタイム例外が発生することを指定します。</span><span class="sxs-lookup"><span data-stu-id="4dd1c-122">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="4dd1c-123">参照</span><span class="sxs-lookup"><span data-stu-id="4dd1c-123">See Also</span></span>  
 [<span data-ttu-id="4dd1c-124">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="4dd1c-124">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="4dd1c-125">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="4dd1c-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
