---
title: '方法: ダイアログ ボックスの結果を返す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 8f754577a355a58060238bbbb487c36aea14658c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545588"
---
# <a name="how-to-return-a-dialog-box-result"></a>方法: ダイアログ ボックスの結果を返す
この例は、呼び出すことによって開かれているウィンドウのダイアログの結果を取得する方法を示します<xref:System.Windows.Window.ShowDialog%2A>です。  
  
## <a name="example"></a>例  
 ダイアログ ボックスを閉じる前にその<xref:System.Windows.Window.DialogResult%2A>でプロパティを設定する必要があります、 <xref:System.Nullable%601> <xref:System.Boolean>ユーザーがダイアログ ボックスを閉じる方法を示すです。 この値がによって返される<xref:System.Windows.Window.ShowDialog%2A> ダイアログ ボックスが閉じられました方法と、その結果、結果を処理する方法を決定するクライアント コードを許可します。  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A> 呼び出して、ウィンドウが開かれた場合にのみ設定できます<xref:System.Windows.Window.ShowDialog%2A>です。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 呼び出す<xref:System.Windows.Window.ShowDialog%2A>すべての windows とユーザー入力イベントを制限なく使用する権限が必要です。
