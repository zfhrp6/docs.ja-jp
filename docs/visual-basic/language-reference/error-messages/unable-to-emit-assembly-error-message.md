---
title: アセンブリを作成できません:&lt;エラー メッセージ&gt;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59288ba7b4cec34cd2266d66aa931e92598e819a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="35efd-102">アセンブリを作成できません:&lt;エラー メッセージ&gt;</span><span class="sxs-lookup"><span data-stu-id="35efd-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="35efd-103">Visual Basic コンパイラでは、リンカー、アセンブリを作成する出力段階でエラーが報告アセンブリ リンカー (Al.exe、Alink とも呼ばれます)、マニフェストを伴うアセンブリを生成するを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="35efd-103">The Visual Basic compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="35efd-104">**エラー ID:** BC30145</span><span class="sxs-lookup"><span data-stu-id="35efd-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="35efd-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="35efd-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="35efd-106">引用符で囲まれたエラー メッセージを確認し、トピックを参照して[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)です。</span><span class="sxs-lookup"><span data-stu-id="35efd-106">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="35efd-107">さらに詳しい説明とアドバイスを参照します。</span><span class="sxs-lookup"><span data-stu-id="35efd-107">for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="35efd-108">アセンブリに手動で署名するかを使用して再試行してください、 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)または[Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md)です。</span><span class="sxs-lookup"><span data-stu-id="35efd-108">Try signing the assembly manually, using either the [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) or the [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
3.  <span data-ttu-id="35efd-109">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="35efd-109">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="35efd-110">アセンブリを手動で署名するには</span><span class="sxs-lookup"><span data-stu-id="35efd-110">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="35efd-111">[Sn.exe (厳密名ツール)] を使用して[Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md)) 公開/秘密キー ペア ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="35efd-111">Use the [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="35efd-112">このファイルは .snk の拡張子を持ちます。</span><span class="sxs-lookup"><span data-stu-id="35efd-112">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="35efd-113">エラーが発生している COM 参照をプロジェクトから削除します。</span><span class="sxs-lookup"><span data-stu-id="35efd-113">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="35efd-114">Windows から**開始** メニューのをポイント**プログラム**、 をポイント**Microsoft Visual Studio 2008**、 をポイント**Visual Studio Tools**、およびをクリックして**Visual Studio 2008 コマンド プロンプト**です。</span><span class="sxs-lookup"><span data-stu-id="35efd-114">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="35efd-115">アセンブリ ラッパーを格納するディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="35efd-115">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="35efd-116">次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="35efd-116">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="35efd-117">コードの一例として、次のように入力することができます。</span><span class="sxs-lookup"><span data-stu-id="35efd-117">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="35efd-118">パスやファイルに空白が含まれている場合には、二重引用符 (") を使用します。</span><span class="sxs-lookup"><span data-stu-id="35efd-118">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="35efd-119">Visual Studio で作成したファイルへの参照を .NET アセンブリを追加します。</span><span class="sxs-lookup"><span data-stu-id="35efd-119">In Visual Studio, add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35efd-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="35efd-120">See Also</span></span>  
 
 <span data-ttu-id="35efd-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)です。</span><span class="sxs-lookup"><span data-stu-id="35efd-121">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 <span data-ttu-id="35efd-122">[Sn.exe (厳密名ツール)][Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="35efd-122">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>  
 [<span data-ttu-id="35efd-123">方法: 公開キーと秘密キーのキー ペアを作成する</span><span class="sxs-lookup"><span data-stu-id="35efd-123">How to: Create a Public-Private Key Pair</span></span>](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [<span data-ttu-id="35efd-124">ご意見</span><span class="sxs-lookup"><span data-stu-id="35efd-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
