---
title: "方法 : MDI 子フォームを配置する"
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
- child forms [Windows Forms], arranging
- MDI [Windows Forms], arranging child forms
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5273327c283f873352f62462cc4be59e4b34351f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-arrange-mdi-child-forms"></a>方法 : MDI 子フォームを配置する
多くの場合、アプリケーションには、並べて表示、重ねて表示、整列など、開いている MDI 子フォームのレイアウトを制御するメニュー コマンドがあります。 <xref:System.Windows.Forms.Form.LayoutMdi%2A> メソッドと <xref:System.Windows.Forms.MdiLayout> 列挙値のいずれかを使用して、MDI 親フォーム内の子フォームを再配置することができます。  
  
 <xref:System.Windows.Forms.MdiLayout> 列挙値は、子フォームを重ねて表示したり、水平方向または垂直方向に並べて表示したり、または MDI フォームの下部に沿って整列された子フォーム アイコンとして表示します。 これらの値が、Windows のコマンドと同じ効果がある**ウィンドウを重ねて表示**、**ウィンドウを並べて表示**、**表示**、および**デスクトップを表示します。**、それぞれします。  
  
 多くの場合、これらのメソッドは、メニュー項目の <xref:System.Windows.Forms.Control.Click> イベントで呼び出されるイベント ハンドラーとして使用されます。 このようにして、テキスト "重ねて表示" を指定したメニュー項目に、MDI 子ウィンドウに対する目的の効果を持たせることができます。  
  
### <a name="to-arrange-child-forms"></a>子フォームを整列させるには  
  
1.  メソッドで、<xref:System.Windows.Forms.Form.LayoutMdi%2A> メソッドを使用して MDI 親フォームの <xref:System.Windows.Forms.MdiLayout> 列挙体を設定します。 次に、MDI 親フォーム (<xref:System.Windows.Forms.MdiLayout.Cascade?displayProperty=nameWithType>) の子ウィンドウに `Form1` 列挙値を使用する例を示します。 列挙体は、イベント ハンドラーの中にコードで使用されて、<xref:System.Windows.Forms.Control.Click>のイベント、**ウィンドウを重ねて表示**メニュー項目。  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    >  使用する <xref:System.Windows.Forms.MdiLayout> 列挙値を変更することで、ウィンドウを並べて表示したり、ウィンドウをアイコンとして並べたりすることもできます。  
  
2.  Visual C# を使用している場合は、フォームのコンストラクターに次のコードを追加して、イベント ハンドラーを登録します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## <a name="see-also"></a>関連項目  
 [マルチ ドキュメント インターフェイス (MDI) アプリケーション](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [方法: MDI 親フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [方法: MDI 子フォームを作成する](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [方法: アクティブな MDI 子フォームを特定する](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [方法: アクティブな MDI 子フォームにデータを送信する](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)
