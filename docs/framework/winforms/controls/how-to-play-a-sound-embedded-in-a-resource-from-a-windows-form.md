---
title: '方法 : Windows フォームからリソースに埋め込まれたサウンドを再生する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sounds [Windows Forms], playing from resources
- resources [Windows Forms], playing sounds
- playing sounds [Windows Forms], from resources
- SoundPlayer class [Windows Forms], playing sounds from resources
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
ms.openlocfilehash: c9dc8499e2d12ed17f9b409a805148d08da894fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532136"
---
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a><span data-ttu-id="0a4e6-102">方法 : Windows フォームからリソースに埋め込まれたサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="0a4e6-102">How to: Play a Sound Embedded in a Resource from a Windows Form</span></span>
<span data-ttu-id="0a4e6-103">使用することができます、<xref:System.Media.SoundPlayer>埋め込みリソースからサウンドを再生するクラス。</span><span class="sxs-lookup"><span data-stu-id="0a4e6-103">You can use the <xref:System.Media.SoundPlayer> class to play a sound from an embedded resource.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a4e6-104">例</span><span class="sxs-lookup"><span data-stu-id="0a4e6-104">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0a4e6-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0a4e6-105">Compiling the Code</span></span>  
 <span data-ttu-id="0a4e6-106">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0a4e6-106">This example requires:</span></span>  
  
 <span data-ttu-id="0a4e6-107">インポート、<xref:System.Media?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="0a4e6-107">Importing the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="0a4e6-108">サウンド ファイルを、埋め込まれたリソースとしてプロジェクトに取り込み。</span><span class="sxs-lookup"><span data-stu-id="0a4e6-108">Including the sound file as an embedded resource in your project.</span></span>  
  
 <span data-ttu-id="0a4e6-109">"\<AssemblyName>" を、サウンド ファイルが埋め込まれているアセンブリの名前に置換。</span><span class="sxs-lookup"><span data-stu-id="0a4e6-109">Replacing "\<AssemblyName>" with the name of the assembly in which the sound file is embedded.</span></span> <span data-ttu-id="0a4e6-110">".dll" というサフィックスは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="0a4e6-110">Do not include the ".dll" suffix.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a4e6-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a4e6-111">See Also</span></span>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="0a4e6-112">方法: Windows フォームからサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="0a4e6-112">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [<span data-ttu-id="0a4e6-113">方法: Windows フォームでサウンドの再生をループする</span><span class="sxs-lookup"><span data-stu-id="0a4e6-113">How to: Loop a Sound Playing on a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
