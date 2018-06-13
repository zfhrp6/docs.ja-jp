---
title: '方法 : イメージを持つ Button を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: 9fb871aa39461329654c0289f00bd3080a633913
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550941"
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
