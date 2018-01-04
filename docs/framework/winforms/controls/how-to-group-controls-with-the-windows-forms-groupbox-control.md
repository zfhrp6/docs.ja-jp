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
ms.workload: dotnet
ms.openlocfilehash: 7ecdb7b8682b13f93f59d1de21552abfa91b8f50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.GroupBox>  
 [GroupBox コントロール](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
