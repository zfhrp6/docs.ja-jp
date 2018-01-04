---
title: "方法 : Windows フォームでサウンドの再生をループする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sound loops
- SoundPlayer class [Windows Forms], play looping
- sounds [Windows Forms], looping
- playing sounds [Windows Forms], looping
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7ade624f57f58a5ec91a5d993375c73d1cc26fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-loop-a-sound-playing-on-a-windows-form"></a><span data-ttu-id="cff89-102">方法 : Windows フォームでサウンドの再生をループする</span><span class="sxs-lookup"><span data-stu-id="cff89-102">How to: Loop a Sound Playing on a Windows Form</span></span>
<span data-ttu-id="cff89-103">サウンドを繰り返し再生するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cff89-103">The following code example plays a sound repeatedly.</span></span> <span data-ttu-id="cff89-104">`stopPlayingButton_Click` イベント ハンドラー内のコードが実行されると、現在再生されているサウンドが停止します。</span><span class="sxs-lookup"><span data-stu-id="cff89-104">When the code in the `stopPlayingButton_Click` event handler runs, any sound currently playing stops.</span></span> <span data-ttu-id="cff89-105">サウンドが再生されていない場合は、何も起こりません。</span><span class="sxs-lookup"><span data-stu-id="cff89-105">If no sound is playing, nothing happens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cff89-106">例</span><span class="sxs-lookup"><span data-stu-id="cff89-106">Example</span></span>  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cff89-107">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="cff89-107">Compiling the Code</span></span>  
 <span data-ttu-id="cff89-108">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cff89-108">This example requires:</span></span>  
  
-   <span data-ttu-id="cff89-109">System アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="cff89-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="cff89-110">ファイル名 `"c:\Windows\Media\chimes.wav"` を有効なファイル名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="cff89-110">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
 <span data-ttu-id="cff89-111">[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法については、「[コマンド ラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」または「[csc.exe を使用したコマンド ラインからのビルド](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cff89-111">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="cff89-112">また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="cff89-112">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="cff89-113">「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="cff89-113">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cff89-114">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="cff89-114">Robust Programming</span></span>  
 <span data-ttu-id="cff89-115">ファイルの操作は、適切な例外処理ブロックで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="cff89-115">File operations should be enclosed within appropriate exception-handling blocks.</span></span>  
  
 <span data-ttu-id="cff89-116">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cff89-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="cff89-117">パス名が不適切である場合。</span><span class="sxs-lookup"><span data-stu-id="cff89-117">The path name is malformed.</span></span> <span data-ttu-id="cff89-118">たとえば、無効な文字が含まれている場合や、空白だけの場合などです (<xref:System.ArgumentException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="cff89-118">For example, it contains characters that are not valid or it is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="cff89-119">パスが読み取り専用である場合 (<xref:System.IO.IOException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="cff89-119">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="cff89-120">パス名が `Nothing` である場合 (<xref:System.ArgumentNullException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="cff89-120">The path name is `Nothing` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="cff89-121">パス名が長すぎる場合 (<xref:System.IO.PathTooLongException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="cff89-121">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="cff89-122">パスが無効である場合 (<xref:System.IO.DirectoryNotFoundException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="cff89-122">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="cff89-123">パスがコロン ":" のみである場合 (<xref:System.NotSupportedException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="cff89-123">The path is only a colon ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cff89-124">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="cff89-124">.NET Framework Security</span></span>  
 <span data-ttu-id="cff89-125">ファイル名からファイルの内容を判断しないでください。</span><span class="sxs-lookup"><span data-stu-id="cff89-125">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="cff89-126">たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="cff89-126">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="cff89-127">アプリケーションでデータを使用する前に、入力をすべて検証してください。</span><span class="sxs-lookup"><span data-stu-id="cff89-127">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cff89-128">参照</span><span class="sxs-lookup"><span data-stu-id="cff89-128">See Also</span></span>  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>  
 [<span data-ttu-id="cff89-129">方法: Windows フォームからサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="cff89-129">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="cff89-130">SoundPlayer クラスの概要</span><span class="sxs-lookup"><span data-stu-id="cff89-130">SoundPlayer Class Overview</span></span>](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)
