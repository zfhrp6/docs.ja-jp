---
title: "方法 : Windows フォームからビープ音を再生する"
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
- sounds [Windows Forms], beep
- Windows Forms, sounds
- sounds [Windows Forms], playing
- forms [Windows Forms], sounds
- examples [Windows Forms], sounds
ms.assetid: 7ea5cded-4888-4f35-8f28-5cab1a55c973
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e214b368b65797100722cb41ad6a77ecd16424de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-a-beep-from-a-windows-form"></a><span data-ttu-id="e8540-102">方法 : Windows フォームからビープ音を再生する</span><span class="sxs-lookup"><span data-stu-id="e8540-102">How to: Play a Beep from a Windows Form</span></span>
<span data-ttu-id="e8540-103">実行時にビープ音を再生する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e8540-103">This example plays a beep at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8540-104">例</span><span class="sxs-lookup"><span data-stu-id="e8540-104">Example</span></span>  
  
```vb  
Public Sub OnePing()  
    Beep()  
End Sub  
```  
  
```csharp  
public void onePing()  
{  
    SystemSounds.Beep.Play();  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="e8540-105">C# コード サンプルで再生するサウンドがによって決定されます、<xref:System.Media.SystemSounds.Beep%2A>システム サウンド設定します。</span><span class="sxs-lookup"><span data-stu-id="e8540-105">The sound played in the C# code sample is determined by the <xref:System.Media.SystemSounds.Beep%2A> system sound setting.</span></span> <span data-ttu-id="e8540-106">詳細については、「<xref:System.Media.SystemSounds>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8540-106">For more information, see <xref:System.Media.SystemSounds>.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8540-107">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e8540-107">Compiling the Code</span></span>  
 <span data-ttu-id="e8540-108">C# の場合、この例への参照が必要です、<xref:System.Media?displayProperty=nameWithType>名前空間。</span><span class="sxs-lookup"><span data-stu-id="e8540-108">For C#, this example requires  a reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8540-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8540-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Beep%2A>  
 <xref:System.Media.SoundPlayer>  
 [<span data-ttu-id="e8540-110">方法: Windows フォームからシステム サウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="e8540-110">How to: Play a System Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-system-sound-from-a-windows-form.md)  
 [<span data-ttu-id="e8540-111">方法: Windows フォームからサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="e8540-111">How to: Play a Sound from a Windows Form</span></span>](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)
