---
title: "/delaysign |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: 19
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
ms.openlocfilehash: bcc819e08ca7731d91dc77dc831060bcf00a4425
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="delaysign"></a><span data-ttu-id="27136-102">T:System.Reflection.AssemblyDelaySignAttribute</span><span class="sxs-lookup"><span data-stu-id="27136-102">/delaysign</span></span>
<span data-ttu-id="27136-103">アセンブリに完全に署名するか、部分的に署名するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="27136-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27136-104">構文</span><span class="sxs-lookup"><span data-stu-id="27136-104">Syntax</span></span>  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="27136-105">引数</span><span class="sxs-lookup"><span data-stu-id="27136-105">Arguments</span></span>  
 <span data-ttu-id="27136-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="27136-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="27136-107">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="27136-107">Optional.</span></span> <span data-ttu-id="27136-108">完全署名されたアセンブリを作成する場合は、`/delaysign-` を使用します。</span><span class="sxs-lookup"><span data-stu-id="27136-108">Use `/delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="27136-109">使用`/delaysign+`かどうかは、署名済みのハッシュのアセンブリと予約のスペースで公開キーを配置します。</span><span class="sxs-lookup"><span data-stu-id="27136-109">Use `/delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="27136-110">既定値は、`/delaysign-` です。</span><span class="sxs-lookup"><span data-stu-id="27136-110">The default is `/delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27136-111">コメント</span><span class="sxs-lookup"><span data-stu-id="27136-111">Remarks</span></span>  
 <span data-ttu-id="27136-112">`/delaysign`オプションも何も起こりませんと共に使用しなければ[/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)または[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)します。</span><span class="sxs-lookup"><span data-stu-id="27136-112">The `/delaysign` option has no effect unless used with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="27136-113">完全署名されたアセンブリを要求すると、コンパイラはマニフェスト (アセンブリ メタデータ) を格納し、秘密キーでそのハッシュに署名するファイルをハッシュします。</span><span class="sxs-lookup"><span data-stu-id="27136-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="27136-114">結果として得られるデジタル署名は、マニフェストを含むファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="27136-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="27136-115">アセンブリに遅延署名がある場合、コンパイラはいないコンピューティングを署名を後で追加できるように、ファイルに署名が予約領域を格納します。</span><span class="sxs-lookup"><span data-stu-id="27136-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="27136-116">たとえばを使用して`/delaysign+`組織内の開発者は、テスト担当者がグローバル アセンブリ キャッシュに登録を使用して、アセンブリの署名のないテスト バージョンを配布できます。</span><span class="sxs-lookup"><span data-stu-id="27136-116">For example, by using `/delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="27136-117">アセンブリに対する作業が完了したら、組織の秘密キーの責任者は、アセンブリを完全署名できます。</span><span class="sxs-lookup"><span data-stu-id="27136-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="27136-118">この区分は、すべての開発者がアセンブリに作業しながら漏洩から組織の秘密キーを保護します。</span><span class="sxs-lookup"><span data-stu-id="27136-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="27136-119">参照してください[の作成と using strong-named Assemblies](https://msdn.microsoft.com/library/xwb8f617)アセンブリへの署名の詳細についてです。</span><span class="sxs-lookup"><span data-stu-id="27136-119">See [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) for more information on signing an assembly.</span></span>  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="27136-120">統合開発環境 Visual Studio で/delaysign を設定するには</span><span class="sxs-lookup"><span data-stu-id="27136-120">To set /delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="27136-121">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="27136-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="27136-122">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="27136-122">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="27136-123">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27136-123">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="27136-124">クリックして、**署名** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="27136-124">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="27136-125">値を設定、**遅延署名のみ**ボックス。</span><span class="sxs-lookup"><span data-stu-id="27136-125">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27136-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="27136-126">See Also</span></span>  
 <span data-ttu-id="27136-127">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="27136-127">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="27136-128"> [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) </span><span class="sxs-lookup"><span data-stu-id="27136-128"> [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) </span></span>  
<span data-ttu-id="27136-129"> [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) </span><span class="sxs-lookup"><span data-stu-id="27136-129"> [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) </span></span>  
<span data-ttu-id="27136-130"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="27136-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
