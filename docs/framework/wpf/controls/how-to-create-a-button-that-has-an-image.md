---
title: "方法 : イメージを持つ Button を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa3aa5454629d53fd8864df6a4f204e22028208f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-button-that-has-an-image"></a>方法 : イメージを持つ Button を作成する
この例では、画像を含める、<xref:System.Windows.Controls.Button>です。  
  
## <a name="example"></a>例  
 次の例では、2 つ作成されます<xref:System.Windows.Controls.Button>コントロール。 1 つ<xref:System.Windows.Controls.Button>テキストを含むイメージが含まれているとします。 イメージは、例のプロジェクト フォルダーのサブフォルダーになって、data という名前のフォルダーには。 ユーザーがクリックしたとき、<xref:System.Windows.Controls.Button>イメージ、バック グラウンド、およびその他のテキストを含む<xref:System.Windows.Controls.Button>を変更します。  
  
 この例で作成<xref:System.Windows.Controls.Button>マークアップを使用して制御しますが、コードを使用して書き込む、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント ハンドラー。  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>関連項目  
 [コントロール](../../../../docs/framework/wpf/controls/index.md)  
 [コントロール ライブラリ](../../../../docs/framework/wpf/controls/control-library.md)
