---
title: '方法: ウィンドウを開く'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 23dc74666d8f47a0fb735d96ad22ed56c96bdbc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545465"
---
# <a name="how-to-open-a-window"></a>方法: ウィンドウを開く
この例では、ウィンドウを開く方法を示します。  
  
## <a name="example"></a>例  
 インスタンス化して、ウィンドウが開き<xref:System.Windows.Window>を呼び出すと、<xref:System.Windows.Window.Show%2A>メソッドです。 <xref:System.Windows.Window.Show%2A> ウィンドウが開き、新しいウィンドウを閉じるを待たずに直ちに返されます。 この種類のウィンドウとも呼ばれます、*モードレス*ウィンドウ、し、ユーザー入力を制限しません。  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 インスタンス化する<xref:System.Windows.Window>安全でないネイティブ メソッドを呼び出す権限が必要です (を参照してください<xref:System.Windows.Window.%23ctor%2A>)。
