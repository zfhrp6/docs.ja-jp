---
title: '方法: ダイアログ ボックスを開く'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
ms.openlocfilehash: 29fe8b0d516f20fcc742b91099a30e368dfe4548
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546362"
---
# <a name="how-to-open-a-dialog-box"></a>方法: ダイアログ ボックスを開く
この例では、ダイアログ ボックスを開く方法を示します。  
  
## <a name="example"></a>例  
 ダイアログ ボックスがインスタンス化して開かれているウィンドウ<xref:System.Windows.Window>を呼び出すと、<xref:System.Windows.Window.ShowDialog%2A>メソッドです。 <xref:System.Windows.Window.ShowDialog%2A> ウィンドウが開き、新しいダイアログ ボックスが閉じられましたまで返されません。 この種類のウィンドウとも呼ばれます、*モーダル*ウィンドウ、し、ユーザー入力を制限します。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 呼び出す<xref:System.Windows.Window.ShowDialog%2A>すべての windows とユーザー入力イベントを制限なく使用する権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 [ダイアログ ボックスの結果を返す](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)
