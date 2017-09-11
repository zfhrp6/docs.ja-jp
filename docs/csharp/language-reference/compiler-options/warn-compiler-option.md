---
title: "-warn (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /warn
dev_langs:
- CSharp
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
caps.latest.revision: 17
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
ms.openlocfilehash: e703060b7cc5f897ddf0b6764e9607460666e92c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="warn-c-compiler-options"></a><span data-ttu-id="eb93d-102">/warn (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="eb93d-102">/warn (C# Compiler Options)</span></span>
<span data-ttu-id="eb93d-103">**/warn** オプションは、コンパイラが表示する警告レベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="eb93d-103">The **/warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb93d-104">構文</span><span class="sxs-lookup"><span data-stu-id="eb93d-104">Syntax</span></span>  
  
```console  
/warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="eb93d-105">引数</span><span class="sxs-lookup"><span data-stu-id="eb93d-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="eb93d-106">コンパイルで表示する警告レベル: 数値が小さいほど重要度が高い警告のみが表示され、数値が大きいほど多くの警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="eb93d-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="eb93d-107">有効な値は 0 から 4 です。</span><span class="sxs-lookup"><span data-stu-id="eb93d-107">Valid values are 0-4:</span></span>  
  
|<span data-ttu-id="eb93d-108">警告レベル</span><span class="sxs-lookup"><span data-stu-id="eb93d-108">Warning level</span></span>|<span data-ttu-id="eb93d-109">説明</span><span class="sxs-lookup"><span data-stu-id="eb93d-109">Meaning</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="eb93d-110">0</span><span class="sxs-lookup"><span data-stu-id="eb93d-110">0</span></span>|<span data-ttu-id="eb93d-111">すべての警告メッセージの出力をオフにします。</span><span class="sxs-lookup"><span data-stu-id="eb93d-111">Turns off emission of all warning messages.</span></span>|  
|<span data-ttu-id="eb93d-112">1</span><span class="sxs-lookup"><span data-stu-id="eb93d-112">1</span></span>|<span data-ttu-id="eb93d-113">重大な警告メッセージを表示します。</span><span class="sxs-lookup"><span data-stu-id="eb93d-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="eb93d-114">2</span><span class="sxs-lookup"><span data-stu-id="eb93d-114">2</span></span>|<span data-ttu-id="eb93d-115">レベル 1 の警告に加え、クラス メンバーの非表示に関する警告など、より重大度の低い特定の警告を表示します。</span><span class="sxs-lookup"><span data-stu-id="eb93d-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="eb93d-116">3</span><span class="sxs-lookup"><span data-stu-id="eb93d-116">3</span></span>|<span data-ttu-id="eb93d-117">レベル 2 の警告に加え、常に `true` または `false` に評価される式に関する警告など、より重大度の低い特定の警告を表示します。</span><span class="sxs-lookup"><span data-stu-id="eb93d-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="eb93d-118">4 (既定)</span><span class="sxs-lookup"><span data-stu-id="eb93d-118">4 (the default)</span></span>|<span data-ttu-id="eb93d-119">レベルの 3 の警告に加え、情報のための警告を表示します。</span><span class="sxs-lookup"><span data-stu-id="eb93d-119">Displays all level 3 warnings plus informational warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb93d-120">コメント</span><span class="sxs-lookup"><span data-stu-id="eb93d-120">Remarks</span></span>  
 <span data-ttu-id="eb93d-121">エラーまたは警告に関する情報を取得するには、ヘルプの索引でエラー コードを検索することができます。</span><span class="sxs-lookup"><span data-stu-id="eb93d-121">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="eb93d-122">エラーまたは警告に関する情報を取得する他の方法については、「[C# コンパイラ エラー](../../../csharp/language-reference/compiler-messages/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb93d-122">For other ways to get information about an error or warning, see [C# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="eb93d-123">すべての警告をエラーとして扱う場合は [/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="eb93d-123">Use [/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="eb93d-124">特定の警告を無効にするには、[/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="eb93d-124">Use [/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="eb93d-125">**/w** は **/warn** の省略形です。</span><span class="sxs-lookup"><span data-stu-id="eb93d-125">**/w** is the short form of **/warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="eb93d-126">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="eb93d-126">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="eb93d-127">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="eb93d-127">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="eb93d-128">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="eb93d-128">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="eb93d-129">**警告レベル** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="eb93d-129">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="eb93d-130">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eb93d-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb93d-131">例</span><span class="sxs-lookup"><span data-stu-id="eb93d-131">Example</span></span>  
 <span data-ttu-id="eb93d-132">`in.cs` をコンパイルして、コンパイラにレベル 1 の警告のみを表示させます。</span><span class="sxs-lookup"><span data-stu-id="eb93d-132">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc /warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb93d-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb93d-133">See Also</span></span>  
 <span data-ttu-id="eb93d-134">[C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="eb93d-134">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="eb93d-135">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="eb93d-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

