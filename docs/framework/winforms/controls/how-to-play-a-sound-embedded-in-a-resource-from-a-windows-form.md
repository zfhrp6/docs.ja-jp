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
# <a name="how-to-play-a-sound-embedded-in-a-resource-from-a-windows-form"></a>方法 : Windows フォームからリソースに埋め込まれたサウンドを再生する
使用することができます、<xref:System.Media.SoundPlayer>埋め込みリソースからサウンドを再生するクラス。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
 インポート、<xref:System.Media?displayProperty=nameWithType>名前空間。  
  
 サウンド ファイルを、埋め込まれたリソースとしてプロジェクトに取り込み。  
  
 "\<AssemblyName>" を、サウンド ファイルが埋め込まれているアセンブリの名前に置換。 ".dll" というサフィックスは含めないでください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Media.SoundPlayer>  
 [方法: Windows フォームからサウンドを再生する](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)  
 [方法: Windows フォームでサウンドの再生をループする](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)
