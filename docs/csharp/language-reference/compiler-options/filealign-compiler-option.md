---
title: "-filealign (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fe2d1df6d88baa2957068514abe728f29cb74636
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="filealign-c-compiler-options"></a><span data-ttu-id="fbe0e-102">/filealign (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="fbe0e-102">/filealign (C# Compiler Options)</span></span>
<span data-ttu-id="fbe0e-103">**/filealign** オプションを使用すると、出力ファイル内のセクションのサイズを指定できます。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-103">The **/filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbe0e-104">構文</span><span class="sxs-lookup"><span data-stu-id="fbe0e-104">Syntax</span></span>  
  
```console  
/filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="fbe0e-105">引数</span><span class="sxs-lookup"><span data-stu-id="fbe0e-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="fbe0e-106">出力ファイル内のセクションのサイズを指定する値です。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="fbe0e-107">有効値は 512、1024、2048、4096、および 8192 です。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="fbe0e-108">これらの値はバイト単位です。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbe0e-109">コメント</span><span class="sxs-lookup"><span data-stu-id="fbe0e-109">Remarks</span></span>  
 <span data-ttu-id="fbe0e-110">各セクションは、**/filealign** 値の倍数である境界上にアラインされます。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-110">Each section will be aligned on a boundary that is a multiple of the **/filealign** value.</span></span> <span data-ttu-id="fbe0e-111">固定の既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-111">There is no fixed default.</span></span> <span data-ttu-id="fbe0e-112">**/filealign** が指定されていない場合、共通言語ランタイムはコンパイル時に既定値を選択します。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-112">If **/filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="fbe0e-113">セクションのサイズを指定すると、出力ファイルのサイズに影響します。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="fbe0e-114">セクションのサイズ変更は、比較的小さなデバイスで実行されるプログラムに対して有効な場合があります。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="fbe0e-115">出力ファイル内のセクションに関する情報を表示するには、[DUMPBIN](/cpp/build/reference/dumpbin-options) を使用します。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-115">Use [DUMPBIN](/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="fbe0e-116">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="fbe0e-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="fbe0e-117">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-117">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="fbe0e-118">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-118">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="fbe0e-119">**[詳細設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-119">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="fbe0e-120">**[ファイルの配置]** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="fbe0e-121">このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fbe0e-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbe0e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbe0e-122">See Also</span></span>  
 [<span data-ttu-id="fbe0e-123">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="fbe0e-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="fbe0e-124">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="fbe0e-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
