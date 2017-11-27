---
title: "方法 : Windows フォーム GroupBox コントロールを使用してコントロールをグループ化する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50d29de04b4e221105bb02e58de01344f13af69f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a>方法 : Windows フォーム GroupBox コントロールを使用してコントロールをグループ化する
Windows フォーム<xref:System.Windows.Forms.GroupBox>コントロールを使用すると、その他のコントロールをグループ化します。 グループ コントロールに次の 3 つの理由があります。  
  
-   わかりやすいユーザー インターフェイスの関連するフォーム要素のビジュアル グループを作成します。  
  
-   プログラムによるグループ化 (たとえばのラジオ ボタン) を作成します。  
  
-   単位として、コントロールをデザイン時に移動します。  
  
### <a name="to-create-a-group-of-controls"></a>コントロールのグループを作成するには  
  
1.  描画、<xref:System.Windows.Forms.GroupBox>フォーム上のコントロールです。  
  
2.  グループ ボックスで各グループ ボックスの内部を描画するには、他のコントロールを追加します。  
  
     グループ ボックス内で囲む必要のある既存のコントロールを使っている場合は、すべてのコントロールを選択して、それらを選択、クリップボードに切り取れません、<xref:System.Windows.Forms.GroupBox>制御、およびグループ ボックスに貼り付けます。 グループ ボックスにドラッグすることもできます。  
  
3.  設定、<xref:System.Windows.Forms.GroupBox.Text%2A>グループ ボックスに適切なキャプションのプロパティです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.GroupBox>  
 [GroupBox コントロール](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
