---
title: "-baseaddress (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f8cc5e19565a0e5044626c4fb8eb9d684fbe0a73
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2017
---
# <a name="baseaddress-c-compiler-options"></a><span data-ttu-id="1bd4f-102">/baseaddress (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="1bd4f-102">/baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="1bd4f-103">**/baseaddress** オプションを使用すると、DLL を読み込む位置に推奨されるベース アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-103">The **/baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="1bd4f-104">このオプションを使用するタイミングと理由の詳細については、[Larry Osterman のブログ](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd4f-105">構文</span><span class="sxs-lookup"><span data-stu-id="1bd4f-105">Syntax</span></span>  
  
```console  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="1bd4f-106">引数</span><span class="sxs-lookup"><span data-stu-id="1bd4f-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="1bd4f-107">DLL のベース アドレス。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-107">The base address for the DLL.</span></span> <span data-ttu-id="1bd4f-108">このアドレスは、10 進数、16 進数、または 8 進数で指定できます。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bd4f-109">コメント</span><span class="sxs-lookup"><span data-stu-id="1bd4f-109">Remarks</span></span>  
 <span data-ttu-id="1bd4f-110">DLL の既定のベース アドレスは、.NET Framework 共通言語ランタイムにより設定されます。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="1bd4f-111">このアドレスの下位ワードは丸められることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="1bd4f-112">たとえば、0x11110001 と指定すると、丸められて 0x11110000 になります。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="1bd4f-113">DLL の署名プロセスを完了するには、-R オプションを指定した SN.EXE を使用します。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1bd4f-114">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="1bd4f-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="1bd4f-115">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-115">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="1bd4f-116">**[ビルド]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="1bd4f-117">**[詳細設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="1bd4f-118">**DLL のベース アドレス** プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="1bd4f-119">このコンパイラ オプションをプログラムによって設定するには、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1bd4f-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd4f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bd4f-120">See Also</span></span>  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="1bd4f-121">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="1bd4f-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="1bd4f-122">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="1bd4f-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
