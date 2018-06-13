---
title: '方法: メッセージ ボックスを開く'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: dd79d69c9b1b54c5158b58ee2f1675e7d11a386a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545637"
---
# <a name="how-to-open-a-message-box"></a>方法: メッセージ ボックスを開く
この例では、メッセージ ボックスを開く方法を示します。  
  
## <a name="example"></a>例  
 メッセージ ボックスは、作成済みのモーダル ダイアログ ボックスのユーザーに情報を表示するためです。 静的なを呼び出すことによって、メッセージ ボックスが開かれた<xref:System.Windows.MessageBox.Show%2A>のメソッド、<xref:System.Windows.MessageBox>クラスです。 ときに<xref:System.Windows.MessageBox.Show%2A>が呼び出されると、メッセージが渡される文字列パラメーターを使用します。 複数のオーバー ロード<xref:System.Windows.MessageBox.Show%2A>をメッセージ ボックスの表示方法を構成すること (を参照してください<xref:System.Windows.MessageBox>)。  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>関連項目  
 [メッセージ ボックスのサンプル](http://go.microsoft.com/fwlink/?LinkID=160023)
