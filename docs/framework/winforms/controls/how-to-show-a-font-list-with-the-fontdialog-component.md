---
title: "方法 : FontDialog コンポーネントを使用してフォントの一覧を表示する"
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
- cpp
helpviewer_keywords:
- fonts [Windows Forms], showing list
- FontDialog component [Windows Forms]
- fonts [Windows Forms], attributes
- Font property [Windows Forms], setting with FontDialog component
- Font dialog box [Windows Forms], displaying
- fonts [Windows Forms], selecting
ms.assetid: 35692c1b-0937-4b7a-9207-1ae6bdc244a0
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd04a44e6f6e3df26a643a8937e20e232e7471a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-show-a-font-list-with-the-fontdialog-component"></a>方法 : FontDialog コンポーネントを使用してフォントの一覧を表示する
[FontDialog](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)コンポーネントにより、ユーザーを幅やサイズなど、表示属性を変更できるだけでなく、フォントを選択します。  
  
 ダイアログ ボックスで選択されているフォントが返されます、<xref:System.Windows.Forms.FontDialog.Font%2A>プロパティです。 したがって、ユーザーが選択されているフォントの利用はプロパティの読み取りと同じくらい簡単です。  
  
### <a name="to-select-font-properties-using-the-fontdialog-component"></a>FontDialog コンポーネントを使用するフォント プロパティを選択するには  
  
1.  ダイアログ ボックスを使用して、表示、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドです。  
  
2.  使用して、<xref:System.Windows.Forms.DialogResult>プロパティ ダイアログ ボックスの終了方法を確認します。  
  
3.  使用して、<xref:System.Windows.Forms.FontDialog.Font%2A>プロパティを目的のフォントを設定します。  
  
     次の例で、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラーが表示されます、<xref:System.Windows.Forms.FontDialog>コンポーネントです。 ときに、フォントを選択し、ユーザーが**[ok]**、<xref:System.Windows.Forms.FontDialog.Font%2A>のプロパティ、<xref:System.Windows.Forms.TextBox>がフォームにコントロールが選択されているフォントに設定します。 この例では、フォームに、<xref:System.Windows.Forms.Button>コントロール、<xref:System.Windows.Forms.TextBox>コントロール、および<xref:System.Windows.Forms.FontDialog>コンポーネントです。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If FontDialog1.ShowDialog() = DialogResult.OK Then  
          TextBox1.Font = FontDialog1.Font  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(fontDialog1.ShowDialog() == DialogResult.OK)  
       {  
          textBox1.Font = fontDialog1.Font;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(fontDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Font = fontDialog1->Font;  
          }  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] および [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) フォームのコンストラクターに次のコードを追加して、イベント ハンドラーを登録します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Forms.FontDialog>  
 [FontDialog コンポーネント](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
