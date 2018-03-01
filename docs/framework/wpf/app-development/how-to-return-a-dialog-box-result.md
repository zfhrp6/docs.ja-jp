---
title: "方法: ダイアログ ボックスの結果を返す"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f8133ffa7be9cb4e0600fc2681402d5e0f7471c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-return-a-dialog-box-result"></a>方法: ダイアログ ボックスの結果を返す
この例は、呼び出すことによって開かれているウィンドウのダイアログの結果を取得する方法を示します<xref:System.Windows.Window.ShowDialog%2A>です。  
  
## <a name="example"></a>例  
 ダイアログ ボックスを閉じる前にその<xref:System.Windows.Window.DialogResult%2A>でプロパティを設定する必要があります、 <xref:System.Nullable%601> <xref:System.Boolean>ユーザーがダイアログ ボックスを閉じる方法を示すです。 この値がによって返される<xref:System.Windows.Window.ShowDialog%2A> ダイアログ ボックスが閉じられました方法と、その結果、結果を処理する方法を決定するクライアント コードを許可します。  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A>呼び出して、ウィンドウが開かれた場合にのみ設定できます<xref:System.Windows.Window.ShowDialog%2A>です。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 呼び出す<xref:System.Windows.Window.ShowDialog%2A>すべての windows とユーザー入力イベントを制限なく使用する権限が必要です。
