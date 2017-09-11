---
title: "-main (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /main
dev_langs:
- CSharp
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eee7ef4698f4b6bf7c90ff8e22a1a3ae106bec35
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="main-c-compiler-options"></a><span data-ttu-id="a91e7-102">/main (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="a91e7-102">/main (C# Compiler Options)</span></span>
<span data-ttu-id="a91e7-103">このオプションは、**Main** メソッドを含むクラスが複数ある場合に、プログラムへのエントリ ポイントを含むクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a91e7-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a91e7-104">構文</span><span class="sxs-lookup"><span data-stu-id="a91e7-104">Syntax</span></span>  
  
```console  
/main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="a91e7-105">引数</span><span class="sxs-lookup"><span data-stu-id="a91e7-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="a91e7-106">**Main** メソッドを含む型です。</span><span class="sxs-lookup"><span data-stu-id="a91e7-106">The type that contains the **Main** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a91e7-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a91e7-107">Remarks</span></span>  
 <span data-ttu-id="a91e7-108">[Main](../../../csharp/programming-guide/main-and-command-args/index.md) メソッドを使用した型がコンパイル対象に 2 つ以上含まれている場合には、プログラムへのエントリ ポイントとして使用する **Main** メソッドがどの型に含まれているかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a91e7-108">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="a91e7-109">このオプションは、.exe ファイルをコンパイルする際に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a91e7-109">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a91e7-110">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="a91e7-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="a91e7-111">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="a91e7-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="a91e7-112">**[アプリケーション]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a91e7-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="a91e7-113">**[スタートアップ オブジェクト]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="a91e7-113">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="a91e7-114">このコンパイラ オプションをプログラムによって設定するには、「<xref:VSLangProj80.ProjectProperties3.StartupObject%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a91e7-114">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a91e7-115">例</span><span class="sxs-lookup"><span data-stu-id="a91e7-115">Example</span></span>  
 <span data-ttu-id="a91e7-116">**Main** メソッドが`Test2` にあることを指定して、`t2.cs` と `t3.cs` をコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="a91e7-116">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs /main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="a91e7-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a91e7-117">See Also</span></span>  
 <span data-ttu-id="a91e7-118">[C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="a91e7-118">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="a91e7-119">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="a91e7-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

