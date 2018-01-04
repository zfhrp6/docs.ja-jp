---
title: "方法 : 実行時にコントロールを非表示にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e28a682c6f3bfc52a293daebeade960c1875bb5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a>方法 : 実行時にコントロールを非表示にする
実行時に表示されているユーザー コントロールを作成する場合もあります。 たとえば、アラーム クロックであるコントロールはアラームが鳴っている場合を除く表示でない可能性があります。 設定これを簡単に行う、<xref:System.Windows.Forms.Control.Visible%2A>プロパティです。 場合、<xref:System.Windows.Forms.Control.Visible%2A>プロパティは`true`コントロールを通常どおりに表示されます。 場合`false`コントロールは表示されません。 コントロール内のコードは、非表示のとき実行可能性がありますも、ユーザー インターフェイスを使用するコントロールと対話することはできません。 ユーザー (マウス クリックなど) の入力にも応答を非表示のコントロールを作成する場合は、透明なコントロールを作成する必要があります。 詳細については、次を参照してください。[制御を透明な背景に与える](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)です。  
  
### <a name="to-make-your-control-invisible-at-run-time"></a>実行時にコントロールを非表示にするには  
  
1.  <xref:System.Windows.Forms.Control.Visible%2A> プロパティを `false` に設定します。  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [方法: コントロールに透明な背景を指定する](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
