---
title: "方法 : ユーザー インターフェイスを持たないコントロールを Windows フォームに追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NonVisualSelection"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コントロール [Windows フォーム], 非可視の"
  - "非表示のコントロール"
  - "非可視のコントロール"
  - "Windows フォーム コントロール, 追加 (フォームに)"
  - "Windows フォーム コントロール, 非可視の"
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : ユーザー インターフェイスを持たないコントロールを Windows フォームに追加する
表示できる形式を持たないコントロール \(コンポーネント\) を使用すると、アプリケーションに機能を追加できます。  ほかのコントロールと異なり、コンポーネントにはユーザー インターフェイスが用意されていません。このため、Windows フォーム デザイナーの領域にコンポーネントを表示する必要はありません。  Windows フォーム デザイナーでは、フォームにコンポーネントを追加すると、すべてのコンポーネントが表示されるフォームの下部に、サイズの変更できるトレイが表示されます。  コンポーネント トレイにコントロールを追加すると、フォームのほかのコントロールの場合と同様に、コンポーネントを選択し、プロパティを設定できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### Windows フォームにコンポーネントを追加するには  
  
1.  フォームを開きます。  詳細については、「[How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/ja-jp/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)」を参照してください。  
  
2.  **ツールボックス**で、コンポーネントをクリックし、フォームにドラッグします。  
  
     コンポーネント トレイにコンポーネントが表示されます。  
  
 または、実行時にフォームにコンポーネントを追加することもできます。  ユーザー インターフェイスを持つコントロールと異なり、表示できる形式を持たないコンポーネントでは、通常、このように処理します。  次の例では、<xref:System.Windows.Forms.Timer> コンポーネントが実行時に追加されます。  [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] には複数の種類のタイマーが用意されています。この場合は、Windows フォームの <xref:System.Windows.Forms.Timer> コンポーネントを使用します。  [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] の各種タイマーの詳細については、「[Introduction to Server\-Based Timers](http://msdn.microsoft.com/ja-jp/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)」を参照してください。  
  
> [!CAUTION]
>  コンポーネントには特有のプロパティが含まれることが多く、コンポーネントを効果的に機能させるにはこれらのプロパティを設定する必要があります。  <xref:System.Windows.Forms.Timer> コンポーネントの場合は、次の例に示されるように、`Interval` プロパティを設定します。  プロジェクトにコンポーネントを追加する場合は、コンポーネントに必要なプロパティを必ず設定してください。  
  
#### プログラムによって、Windows フォームにコンポーネントを追加するには  
  
1.  コードで <xref:System.Windows.Forms.Timer> クラスのインスタンスを作成します。  
  
2.  `Interval` プロパティを設定して、タイマー刻みの間隔を決定します。  
  
3.  コンポーネントに必要なその他のプロパティを設定します。  
  
     `Interval` プロパティを設定して <xref:System.Windows.Forms.Timer> を作成するコードを次に示します。  
  
    ```vb  
    Public Sub CreateTimer()  
       Dim timerKeepTrack As New System.Windows.Forms.Timer  
       timerKeepTrack.Interval = 1000  
    End Sub  
  
    ```  
  
    ```csharp  
    public void createTimer()  
    {  
       System.Windows.Forms.Timer timerKeepTrack = new  
           System.Windows.Forms.Timer();  
       timerKeepTrack.Interval = 1000;  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void createTimer()  
       {  
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew  
             System::Windows::Forms::Timer();  
          timerKeepTrack->Interval = 1000;  
       }  
    ```  
  
    > [!IMPORTANT]
    >  悪意のあるユーザー コントロールを参照することにより、ローカル コンピューターがネットワークを通じてセキュリティ上のリスクを負う可能性があります。  このことが問題になるのは、悪意のあるユーザーが有害なカスタム コントロールを作成していて、開発者が自分のプロジェクトに誤ってそれを追加してしまった場合です。  
  
## 参照  
 [Windows フォーム コントロール](../../../../docs/framework/winforms/controls/index.md)   
 [方法 : Windows フォームにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)   
 [方法 : Windows フォームに ActiveX コントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)   
 [方法 : Windows フォーム間でコントロールをコピーする](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)   
 [Windows フォームへのコントロールの追加](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)   
 [各 Windows フォーム コントロールのラベル設定とショートカットの作成](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Windows フォーム コントロールの機能別一覧](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)