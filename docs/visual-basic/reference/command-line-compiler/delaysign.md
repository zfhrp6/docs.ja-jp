---
title: -delaysign
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d659e97f3b3a360456a1fcdaa9756934bb096334
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-delaysign"></a><span data-ttu-id="b11be-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="b11be-102">-delaysign</span></span>
<span data-ttu-id="b11be-103">アセンブリに完全に署名するか、部分的に署名するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b11be-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b11be-104">構文</span><span class="sxs-lookup"><span data-stu-id="b11be-104">Syntax</span></span>  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b11be-105">引数</span><span class="sxs-lookup"><span data-stu-id="b11be-105">Arguments</span></span>  
 <span data-ttu-id="b11be-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="b11be-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="b11be-107">任意。</span><span class="sxs-lookup"><span data-stu-id="b11be-107">Optional.</span></span> <span data-ttu-id="b11be-108">完全署名されたアセンブリを作成する場合は、`-delaysign-` を使用します。</span><span class="sxs-lookup"><span data-stu-id="b11be-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="b11be-109">使用して`-delaysign+`かどうかは、署名のハッシュのアセンブリと予約のスペースで公開キーを配置します。</span><span class="sxs-lookup"><span data-stu-id="b11be-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="b11be-110">既定値は、`-delaysign-` です。</span><span class="sxs-lookup"><span data-stu-id="b11be-110">The default is `-delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b11be-111">コメント</span><span class="sxs-lookup"><span data-stu-id="b11be-111">Remarks</span></span>  
 <span data-ttu-id="b11be-112">`-delaysign`オプションも何も起こりませんと共に使用しなければ[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)または[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)です。</span><span class="sxs-lookup"><span data-stu-id="b11be-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="b11be-113">アセンブリに完全に署名するように指定すると、コンパイラはマニフェスト (アセンブリ メタデータ) を含むファイルをハッシュし、秘密キーでそのハッシュに署名します。</span><span class="sxs-lookup"><span data-stu-id="b11be-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="b11be-114">結果として得られるデジタル署名は、マニフェストを含むファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b11be-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="b11be-115">アセンブリに遅延署名がある場合、コンパイラはないを計算し、署名を後で追加できるように、ファイルに署名が予約領域を格納します。</span><span class="sxs-lookup"><span data-stu-id="b11be-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="b11be-116">たとえばを使用して`-delaysign+`組織内の開発者は、テスト担当者がグローバル アセンブリ キャッシュに登録して使用するアセンブリのバージョンの符号なしのテストを配布できます。</span><span class="sxs-lookup"><span data-stu-id="b11be-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="b11be-117">アセンブリでの作業が完了したら、組織の秘密キーの責任者は、アセンブリを完全署名できます。</span><span class="sxs-lookup"><span data-stu-id="b11be-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="b11be-118">この区分は、すべての開発者が、アセンブリに作業しながら、情報の漏えいから組織の秘密キーを保護します。</span><span class="sxs-lookup"><span data-stu-id="b11be-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="b11be-119">参照してください[作成と使用](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)アセンブリに署名する方法についてです。</span><span class="sxs-lookup"><span data-stu-id="b11be-119">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="b11be-120">Visual Studio 統合開発環境で-delaysign を設定するには</span><span class="sxs-lookup"><span data-stu-id="b11be-120">To set -delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="b11be-121">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="b11be-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b11be-122">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b11be-122">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="b11be-123">**[署名]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b11be-123">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="b11be-124">値を設定、**遅延署名のみ**ボックス。</span><span class="sxs-lookup"><span data-stu-id="b11be-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b11be-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="b11be-125">See Also</span></span>  
 [<span data-ttu-id="b11be-126">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="b11be-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b11be-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="b11be-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="b11be-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="b11be-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [<span data-ttu-id="b11be-129">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="b11be-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
