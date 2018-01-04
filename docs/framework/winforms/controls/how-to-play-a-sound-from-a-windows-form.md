---
title: "方法 : Windows フォームからサウンドを再生する"
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
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31c9495e22af0e06869d54f02d4ce0e866e28dbb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="f0d9d-102">方法 : Windows フォームからサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="f0d9d-102">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="f0d9d-103">この例では、実行時に指定されたパスでサウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-103">This example plays a sound at a given path at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0d9d-104">例</span><span class="sxs-lookup"><span data-stu-id="f0d9d-104">Example</span></span>  
  
```vb  
Sub PlaySimpleSound()  
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")  
End Sub  
```  
  
```csharp  
private void playSimpleSound()  
{  
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");  
    simpleSound.Play();  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f0d9d-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f0d9d-105">Compiling the Code</span></span>  
 <span data-ttu-id="f0d9d-106">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-106">This example requires:</span></span>  
  
-   <span data-ttu-id="f0d9d-107">ファイル名 `"c:\Windows\Media\chimes.wav"` を有効なファイル名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-107">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>  
  
-   <span data-ttu-id="f0d9d-108">(C#)参照、<xref:System.Media?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-108">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f0d9d-109">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="f0d9d-109">Robust Programming</span></span>  
 <span data-ttu-id="f0d9d-110">ファイルの操作は、適切な構造の例外処理ブロックで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-110">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>  
  
 <span data-ttu-id="f0d9d-111">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f0d9d-112">パス名が不適切である場合。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-112">The path name is malformed.</span></span> <span data-ttu-id="f0d9d-113">たとえば、不正な文字が含まれている場合や、空白だけの場合などがその例です (<xref:System.ArgumentException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-113">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>  
  
-   <span data-ttu-id="f0d9d-114">パスが読み取り専用である場合 (<xref:System.IO.IOException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>  
  
-   <span data-ttu-id="f0d9d-115">パス名が `null` である場合 (<xref:System.ArgumentNullException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-115">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
-   <span data-ttu-id="f0d9d-116">パス名が長すぎる場合 (<xref:System.IO.PathTooLongException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
-   <span data-ttu-id="f0d9d-117">パスが無効である場合 (<xref:System.IO.DirectoryNotFoundException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-117">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>  
  
-   <span data-ttu-id="f0d9d-118">パスがコロンにのみ、":"(<xref:System.NotSupportedException>クラス)。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-118">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f0d9d-119">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f0d9d-119">.NET Framework Security</span></span>  
 <span data-ttu-id="f0d9d-120">ファイル名からファイルの内容を判断しないでください。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="f0d9d-121">たとえば、`Form1.vb` というファイルは Visual Basic のソース ファイルではない可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="f0d9d-122">アプリケーションでデータを使用する前に、入力をすべて検証してください。</span><span class="sxs-lookup"><span data-stu-id="f0d9d-122">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d9d-123">参照</span><span class="sxs-lookup"><span data-stu-id="f0d9d-123">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="f0d9d-124">方法: Windows フォーム内でサウンドを非同期的に読み込む</span><span class="sxs-lookup"><span data-stu-id="f0d9d-124">How to: Load a Sound Asynchronously within a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)  
 
