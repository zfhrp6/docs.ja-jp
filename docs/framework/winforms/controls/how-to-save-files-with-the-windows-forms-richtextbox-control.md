---
title: '方法 : Windows フォームの RichTextBox コントロールを使用してファイルを保存する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: c50b2f3309c1f811b29e824327a709e2cc4bd791
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536196"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>方法 : Windows フォームの RichTextBox コントロールを使用してファイルを保存する
Windows フォーム<xref:System.Windows.Forms.RichTextBox>コントロールがいくつかの形式のいずれかで表示される情報を書き込むことができます。  
  
-   プレーンテキスト  
  
-   Unicode のプレーン テキスト  
  
-   リッチ テキスト形 (式 RTF)  
  
-   OLE オブジェクトの代わりにスペースを含む RTF  
  
-   OLE オブジェクトのテキスト表現でプレーン テキスト  
  
 ファイルを保存するを呼び出して、<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>メソッドです。 使用することも、 **SaveFile**メソッド データをストリームに保存します。 詳細については、「<xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>」を参照してください。  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a>コントロールの内容をファイルに保存するには  
  
1.  保存するファイルのパスを決定します。  
  
     これを行う実際のアプリケーションで、通常使用、<xref:System.Windows.Forms.SaveFileDialog>コンポーネントです。 概要については、次を参照してください。 [SaveFileDialog コンポーネントの概要](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md)です。  
  
2.  呼び出す、<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>のメソッド、<xref:System.Windows.Forms.RichTextBox>制御、ファイルを保存して、必要に応じてファイルの種類を指定します。 唯一の引数としてファイル名を持つメソッドを呼び出す場合は、rtf 形式で、ファイルが保存されます。 別の種類のファイルを指定するには、2 番目の引数として <xref:System.Windows.Forms.RichTextBoxStreamType> 列挙型の値を指定します。  
  
     リッチ テキスト ファイルの場所は次の例では、パスを設定、**マイ ドキュメント**フォルダーです。 この場所は、Windows オペレーティング システムを実行しているほとんどのコンピューターがこのフォルダーを含めることを想定するために使用されます。 この場所を選択すると、最小限のシステム アクセスのレベルを持つユーザーは、アプリケーションを安全に実行もできます。 次の例にフォームを前提としています、<xref:System.Windows.Forms.RichTextBox>コントロールが既に追加されています。  
  
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
    >  次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。 アプリケーション ファイルを作成する場合は、フォルダーの作成アクセスが必要です。 アクセス許可は、アクセス制御リストを使って設定します。 ファイルが既に存在する場合、アプリケーションには、書き込みアクセスだけより低い権限が必要があります。 可能な展開時に、ファイルを作成し、のみ 1 つのファイルに対する読み取りアクセス権を付与ではなくフォルダーのアクセスを作成する方が安全です。 また、ルート フォルダーや Program Files フォルダーにデータを書き込むよりも、ユーザー フォルダーに書き込む方が安全です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox コントロール](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
