---
title: "方法 : Windows フォームの RichTextBox コントロールを使用してファイルを保存する | Microsoft Docs"
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
  - ".rtf ファイル, 保存 (RichTextBox コントロールで)"
  - "例 [Windows フォーム], テキスト ボックス"
  - "ファイル, 保存 (RichTextBox コントロールを使用して)"
  - "RichTextBox コントロール [Windows フォーム], 保存 (ファイルを)"
  - "RTF ファイル, 保存 (RichTextBox コントロールで)"
  - "保存 (ファイルを)"
  - "保存 (ファイルを), RichTextBox コントロール"
  - "テキスト ファイル, 保存 (RichTextBox コントロールから)"
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォームの RichTextBox コントロールを使用してファイルを保存する
Windows フォームの <xref:System.Windows.Forms.RichTextBox> コントロールでは、表示している情報を次のいずれかの形式でファイルに書き込むことができます。  
  
-   書式なしテキスト  
  
-   Unicode の書式なしテキスト  
  
-   リッチ テキスト形式 \(RTF: Rich Text Format\)  
  
-   OLE オブジェクトをスペースに置き換えた RTF  
  
-   OLE オブジェクトをテキストで表示した書式なしテキスト  
  
 ファイルを保存するには、<xref:System.Windows.Forms.RichTextBox.SaveFile%2A> メソッドを呼び出します。  また、**SaveFile** メソッドを使用してストリームにデータを保存することもできます。  詳細については、<xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29> のトピックを参照してください。  
  
### コントロールの内容をファイルに保存するには  
  
1.  保存するファイルのパスを決定します。  
  
     実際のアプリケーションでこれを行うには、通常、<xref:System.Windows.Forms.SaveFileDialog> コンポーネントを使用します。  概要については、「[SaveFileDialog コンポーネントの概要](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md)」を参照してください。  
  
2.  保存するファイルと、必要に応じてファイルの種類を指定して、<xref:System.Windows.Forms.RichTextBox> コントロールの <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> メソッドを呼び出します。  引数にファイル名だけを指定してメソッドを呼び出すと、ファイルは RTF として保存されます。  別の種類のファイルを指定するには、2 番目の引数として <xref:System.Windows.Forms.RichTextBoxStreamType> 列挙型の値を指定します。  
  
     次の例では、リッチ テキスト ファイルの場所に対するパスとして **My Documents** フォルダーが設定されています。  この場所を使用するのは、Windows オペレーティング システムを実行するコンピューターには、通常このディレクトリが存在すると考えられるためです。  また、この場所を選択すると、ユーザーは最小限のシステム アクセス レベルでアプリケーションを安全に実行できます。  次の例は、既に <xref:System.Windows.Forms.RichTextBox> コントロールが追加されたフォームを想定しています。  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。  アプリケーションでファイルを作成する必要がある場合は、フォルダーに対してファイルの作成アクセスが必要です。  アクセス許可は、アクセス制御リストを使用して設定します。  ファイルが既に存在する場合、アプリケーションに必要なのは、より低い権限である書き込みアクセス許可だけです。  可能な場合は、配置時にファイルを作成し、フォルダーにはファイルの作成アクセスを許可せず、1 つのファイルだけに読み取りアクセスを許可する方が安全です。  また、ルート フォルダーや Program Files フォルダーにデータを書き込むよりも、ユーザー フォルダーに書き込む方が安全です。  
  
## 参照  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.RichTextBox>   
 [RichTextBox コントロール](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)