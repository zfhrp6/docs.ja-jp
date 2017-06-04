---
title: "方法 : Windows フォームの RichTextBox コントロールにファイルを読み込む | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "テキスト ボックス、ファイルの表示"
  - "例 [Windows フォーム]、テキスト ボックス"
  - ".rtf ファイル、RichTextBox コントロールで開く"
  - "RTF ファイル、RichTextBox コントロールで開く"
  - "テキスト ファイル、RichTextBox コントロールで表示"
  - ".rtf ファイル、RichTextBox コントロールで表示"
  - "RichTextBox コントロール [Windows フォーム], ファイルを開く"
  - "RTF ファイル、RichTextBox コントロールで表示"
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォームの RichTextBox コントロールにファイルを読み込む
Windows フォームの <xref:System.Windows.Forms.RichTextBox> コントロールには、プレーン テキスト、Unicode のプレーン テキスト、リッチ テキスト形式 \(RTF\) ファイルを表示できます。 それには、<xref:System.Windows.Forms.RichTextBox.LoadFile%2A> メソッドを呼び出します。 また、<xref:System.Windows.Forms.RichTextBox.LoadFile%2A> メソッドを使用してストリームからデータを読み込むこともできます。 詳細については、「<xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>」を参照してください。  
  
### RichTextBox コントロールにファイルを読み込むには  
  
1.  <xref:System.Windows.Forms.OpenFileDialog> コンポーネントを使用して、開くファイルのパスを決定します。 概要については、「[OpenFileDialog コンポーネントの概要](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md)」を参照してください。  
  
2.  読み込むファイルと、必要に応じてファイルの種類を指定して、<xref:System.Windows.Forms.RichTextBox> コントロールの <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> メソッドを呼び出します。 次の例では、読み込むファイルは <xref:System.Windows.Forms.OpenFileDialog> コンポーネントの <xref:System.Windows.Forms.FileDialog.FileName%2A> プロパティから取得されます。 引数にファイル名だけを指定してメソッドを呼び出すと、ファイルの種類は RTF と見なされます。 別の種類のファイルを指定するには、2 番目の引数として <xref:System.Windows.Forms.RichTextBoxStreamType> 列挙型の値を指定します。  
  
     次の例では、ボタンがクリックされたときに <xref:System.Windows.Forms.OpenFileDialog> コンポーネントが表示されます。 次に、選択されたファイルが開き、<xref:System.Windows.Forms.RichTextBox> コントロールに表示されます。 この例ではフォームにボタン `btnOpenFile` があることを前提としています。  
  
    ```vb  
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles btnOpenFile.Click  
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then  
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _  
              RichTextBoxStreamType.RichText)  
          End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void btnOpenFile_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == DialogResult.OK)  
       {  
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);  
       }  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void btnOpenFile_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          if(openFileDialog1->ShowDialog() == DialogResult::OK)  
          {  
             richTextBox1->LoadFile(openFileDialog1->FileName,  
                RichTextBoxStreamType::RichText);  
          }  
       }  
    ```  
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  このプロセスを実行するには、アセンブリに対して <xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName> クラスで特権レベルが許可されていることが必要な場合があります。 部分的に信頼されたコンテキストで実行している場合、プロセスは、特権がないため例外をスローする可能性があります。 詳細については、「[コード アクセス セキュリティの基礎](../../../../docs/framework/misc/code-access-security-basics.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox コントロール](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)