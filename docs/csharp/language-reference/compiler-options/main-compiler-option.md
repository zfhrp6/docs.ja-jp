---
title: -main (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 2df02200578979f9a613f43dc92cc9e7b0cb430e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212421"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="dfd88-102">-main (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="dfd88-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="dfd88-103">このオプションは、**Main** メソッドを含むクラスが複数ある場合に、プログラムへのエントリ ポイントを含むクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="dfd88-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfd88-104">構文</span><span class="sxs-lookup"><span data-stu-id="dfd88-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="dfd88-105">引数</span><span class="sxs-lookup"><span data-stu-id="dfd88-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="dfd88-106">**Main** メソッドを含む型です。</span><span class="sxs-lookup"><span data-stu-id="dfd88-106">The type that contains the **Main** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfd88-107">コメント</span><span class="sxs-lookup"><span data-stu-id="dfd88-107">Remarks</span></span>  
 <span data-ttu-id="dfd88-108">[Main](../../../csharp/programming-guide/main-and-command-args/index.md) メソッドを使用した型がコンパイル対象に 2 つ以上含まれている場合には、プログラムへのエントリ ポイントとして使用する **Main** メソッドがどの型に含まれているかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="dfd88-108">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="dfd88-109">このオプションは、.exe ファイルをコンパイルする際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="dfd88-109">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="dfd88-110">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="dfd88-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="dfd88-111">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="dfd88-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="dfd88-112">**[アプリケーション]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dfd88-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="dfd88-113">**[スタートアップ オブジェクト]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="dfd88-113">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="dfd88-114">このコンパイラ オプションをプログラムによって設定するには、「<xref:VSLangProj80.ProjectProperties3.StartupObject%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dfd88-114">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfd88-115">例</span><span class="sxs-lookup"><span data-stu-id="dfd88-115">Example</span></span>  
 <span data-ttu-id="dfd88-116">**Main** メソッドが`Test2` にあることを指定して、`t2.cs` と `t3.cs` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="dfd88-116">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfd88-117">参照</span><span class="sxs-lookup"><span data-stu-id="dfd88-117">See Also</span></span>  
 [<span data-ttu-id="dfd88-118">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="dfd88-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="dfd88-119">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="dfd88-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
