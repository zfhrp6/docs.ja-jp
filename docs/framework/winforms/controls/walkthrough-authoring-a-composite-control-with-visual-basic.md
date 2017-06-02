---
title: "チュートリアル : Visual Basic による複合コントロールの作成 | Microsoft Docs"
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
  - "複合コントロール, 作成"
  - "コントロール [Windows フォーム], 複合コントロール"
  - "カスタム コントロール [Visual Basic]"
  - "カスタム コントロール [Windows フォーム], 作成"
  - "ユーザー コントロール [Visual Basic]"
  - "ユーザー コントロール [Windows フォーム], 作成 (Visual Basic を使用した)"
  - "UserControl クラス, チュートリアル"
ms.assetid: f50e270e-4db2-409a-8319-6db6ca5c7daf
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# チュートリアル : Visual Basic による複合コントロールの作成
複合コントロールは、カスタム グラフィカル インターフェイスの作成と再利用のための手段を提供します。  複合コントロールは、基本的には表示できる形式を持つコンポーネントです。  そのため、ユーザー コントロールは、1 つ以上の Windows フォーム コントロール、コンポーネント、またはコードのブロックから構成でき、ユーザー入力を検査したり、表示プロパティを変更したり、作成者によって要求されるその他のタスクを実行したりすることで機能を拡張できます。  複合コントロールは、他のコントロールと同じ方法で Windows フォームに配置できます。  このチュートリアルの前半では、`ctlClock` という名前の単純な複合コントロールを作成します。  後半では、継承によって `ctlClock` の機能を拡張します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## プロジェクトの作成  
 新しいプロジェクトを作成するときには、その名前を指定することにより、ルート名前空間、アセンブリ名、およびプロジェクト名を設定し、既定のコンポーネントが正しい名前空間に含まれるようにします。  
  
#### ctlClockLib コントロール ライブラリおよび ctlClock コントロールを作成するには  
  
1.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックして **\[新しいプロジェクト\]** ダイアログ ボックスを表示します。  
  
2.  [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] プロジェクトの一覧の **\[Windows コントロール ライブラリ\]** プロジェクト テンプレートをクリックし、**\[プロジェクト名\]** ボックスに「`ctlClockLib`」と入力して、**\[OK\]** をクリックします。  
  
     プロジェクト名 `ctlClockLib` は、既定でルート名前空間にも割り当てられます。  ルート名前空間は、アセンブリ内のコンポーネント名の修飾に使用されます。  たとえば、`ctlClock` という名前のコンポーネントが 2 つのアセンブリに含まれる場合は、`ctlClockLib.ctlClock` という形で目的の `ctlClock` コンポーネントを指定できます。  
  
3.  ソリューション エクスプローラーで、**UserControl1.vb** を右クリックし、**\[名前の変更\]** をクリックします。  ファイル名を「`ctlClock.vb`」に変更します。  コード要素 "UserControl1" へのすべての参照の名前を変更するかどうかを確認するダイアログ ボックスが表示されたら、**\[はい\]** をクリックします。  
  
    > [!NOTE]
    >  既定では、複合コントロールはシステムによって提供される <xref:System.Windows.Forms.UserControl> クラスを継承します。  <xref:System.Windows.Forms.UserControl> クラスは、すべての複合コントロールに必要な機能を提供し、標準のメソッドおよびプロパティを実装します。  
  
4.  **\[ファイル\]** メニューの **\[すべてを保存\]** をクリックして、プロジェクトを保存します。  
  
## 複合コントロールへの Windows コントロールおよびコンポーネントの追加  
 ビジュアル インターフェイスは、複合コントロールの基本的な部分です。  このビジュアル インターフェイスは、デザイナー画面に 1 つ以上の Windows コントロールを追加することによって実装されます。  次の例では、複合コントロールに Windows コントロールを取り込んで、機能を実装するコードを記述します。  
  
#### 複合コントロールに Label と Timer を追加するには  
  
1.  ソリューション エクスプローラーで **ctlClock.vb** を右クリックし、**\[デザイナーの表示\]** をクリックします。  
  
2.  ツールボックスの **\[コモン コントロール\]** ノードを展開し、**\[Label\]** をダブルクリックします。  
  
     `Label1` という名前の <xref:System.Windows.Forms.Label> がデザイナー画面のコントロールに追加されます。  
  
3.  デザイナーで **Label1** をクリックします。  プロパティ ウィンドウで、次のプロパティを設定します。  
  
    |プロパティ|変更後の値|  
    |-----------|-----------|  
    |**名前**|`lblDisplay`|  
    |**テキスト**|`(空白)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  **ツールボックス**の **\[コンポーネント\]** ノードを展開し、**\[Timer\]** をダブルクリックします。  
  
     <xref:System.Windows.Forms.Timer> はコンポーネントであるため、実行時には表示できる形式を持ちません。  このため、デザイナー画面にはコントロールと共には表示されず、コンポーネント デザイナー \(デザイナー画面の下部にあるトレイ\) に表示されます。  
  
5.  コンポーネント デザイナーで、**\[Timer1\]** をクリックし、<xref:System.Windows.Forms.Timer.Interval%2A> プロパティを `1000`、<xref:System.Windows.Forms.Timer.Enabled%2A> プロパティを `True` に設定します。  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> プロパティは、タイマー コンポーネントが時を刻む頻度を制御します。  `Timer1` が時を刻むたびに、`Timer1_Tick` イベントのコードが実行されます。  このプロパティは、タイマーが何ミリ秒ごとに時を刻むかを表しています。  
  
6.  コンポーネント デザイナーで、**\[Timer1\]** をダブルクリックして、`ctlClock` の `Timer1_Tick` イベントに移動します。  
  
7.  コードを次のコード サンプルのように変更します。  アクセス修飾子を必ず `Private` から `Protected` に変更してください。  
  
     \[Visual Basic\]  
  
    ```  
    Protected Sub Timer1_Tick(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles Timer1.Tick  
        ' Causes the label to display the current time.    
        lblDisplay.Text = Format(Now, "hh:mm:ss")  
    End Sub  
    ```  
  
     このコードは、現在の時刻を `lblDisplay` に表示します。  `Timer1` の間隔は 1000 に設定されているため、このイベントは `1000` ミリ秒ごとに発生します。したがって、現在の時刻は 1 秒ごとに更新されます。  
  
8.  メソッドをオーバーライドできるように変更します。  詳細については、後の「ユーザー コントロールからの継承」を参照してください。  
  
     \[Visual Basic\]  
  
    ```  
    Protected Overridable Sub Timer1_Tick(ByVal sender As Object, ByVal _  
        e As System.EventArgs) Handles Timer1.Tick  
    ```  
  
9. **\[ファイル\]** メニューの **\[すべてを保存\]** をクリックして、プロジェクトを保存します。  
  
## 複合コントロールへのプロパティの追加  
 現在、クロック コントロールは、それぞれが固有のプロパティ セットを持つ <xref:System.Windows.Forms.Label> コントロールと <xref:System.Windows.Forms.Timer> コンポーネントをカプセル化しています。  各コントロールのプロパティは、コントロールの後続のユーザーからはアクセスできませんが、適切なコード ブロックを作成することによってカスタム プロパティを作成および公開できます。  次の手順では、ユーザーが背景とテキストの色を変更できるようにするプロパティをコントロールに追加します。  
  
#### 複合コントロールにプロパティを追加するには  
  
1.  ソリューション エクスプローラーで **ctlClock.vb** を右クリックし、**\[コードの表示\]** をクリックします。  
  
     コントロールのコード エディターが表示されます。  
  
2.  `Public Class ctlClock` ステートメントを探します。  この行の直後に、次のコードを追加します。  
  
     \[Visual Basic\]  
  
    ```  
    Private colFColor as Color  
    Private colBColor as Color  
    ```  
  
     これらのステートメントは、作成するプロパティの値を格納するために使用するプライベート変数を作成します。  
  
3.  手順 2. の変数宣言の下に次のコードを挿入します。  
  
     \[Visual Basic\]  
  
    ```  
    ' Declares the name and type of the property.  
    Property ClockBackColor() as Color  
        ' Retrieves the value of the private variable colBColor.  
        Get  
            Return colBColor  
        End Get  
        ' Stores the selected value in the private variable colBColor, and   
        ' updates the background color of the label control lblDisplay.  
        Set(ByVal value as Color)  
            colBColor = value  
            lblDisplay.BackColor = colBColor     
        End Set  
  
    End Property  
    ' Provides a similar set of instructions for the foreground color.  
    Property ClockForeColor() as Color  
        Get  
            Return colFColor  
        End Get  
        Set(ByVal value as Color)  
            colFColor = value  
            lblDisplay.ForeColor = colFColor  
        End Set  
    End Property  
    ```  
  
     上記のコードは、`Property` ステートメントを呼び出すことにより、このコントロールを今後使用するユーザーが `ClockForeColor` および `ClockBackColor` という 2 つのカスタム プロパティを使用できるようにします。  `Get` ステートメントと `Set` ステートメントは、プロパティに適切な機能を実装するコードと共に、プロパティ値の格納と取得の機能を提供します。  
  
4.  **\[ファイル\]** メニューの **\[すべてを保存\]** をクリックして、プロジェクトを保存します。  
  
## コントロールのテスト  
 コントロールはスタンドアロン プロジェクトではないため、コンテナーでホストする必要があります。  コントロールの実行時の動作をテストし、**ユーザー コントロール テスト コンテナー**でそのプロパティを実行します。  詳細については、「[方法 : UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。  
  
#### コントロールをテストするには  
  
1.  F5 キーを押してプロジェクトをビルドし、**ユーザー コントロール テスト コンテナー**でコントロールを実行します。  
  
2.  テスト コンテナーのプロパティ グリッドで、`ClockBackColor` プロパティを選択し、ドロップダウン矢印をクリックしてカラー パレットを表示します。  
  
3.  任意の色をクリックして選択します。  
  
     コントロールの背景色が、選択した色に変更されます。  
  
4.  同様なイベントのシーケンスを使用して、`ClockForeColor` プロパティが予想どおりに機能することを確認します。  
  
5.  **\[閉じる\]** をクリックして **\[ユーザー コントロール テスト コンテナー\]** を閉じます。  
  
     このセクションと前のセクションでは、コンポーネントと Windows コントロールをコードと結合し、複合コントロールの形式にパッケージ化してカスタム機能を提供する方法を説明しました。  複合コントロールのプロパティを公開し、完了後にコントロールをテストする方法を学びました。  次のセクションでは、`ctlClock` をベースとして継承した複合コントロールを構築する方法を学びます。  
  
## 複合コントロールからの継承  
 前のセクションでは、再利用可能な複合コントロールに Windows コントロール、コンポーネント、およびコードを組み込む方法を学びました。  この複合コントロールをベースにして、他のコントロールを作成できます。  基本クラスからクラスを派生するプロセスは*継承*と呼ばれます。  このセクションでは、`ctlAlarmClock` という名前の複合コントロールを作成します。  このコントロールは、親コントロールである `ctlClock` から派生します。  ここでは、親のメソッドをオーバーライドし、新しいメソッドおよびプロパティを追加することにより、`ctlClock` の機能を拡張する方法を学びます。  
  
 継承コントロールの作成の最初の手順は、親コントロールからの派生です。  これにより、親コントロールのプロパティ、メソッド、およびグラフィカル特性をすべて持つ新しいコントロールが作成されます。このコントロールに基づいて、新しい機能を追加したり機能を変更したりできます。  
  
#### 継承コントロールを作成するには  
  
1.  ソリューション エクスプローラーで、**\[ctlClockLib\]** を右クリックします。**\[追加\]** をポイントし、**\[ユーザー コントロール\]** をクリックします。  
  
     **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
2.  **\[継承されたユーザー コントロール\]** テンプレートを選択します。  
  
3.  **\[ファイル名\]** ボックスに「`ctlAlarmClock.vb`」と入力し、**\[追加\]** をクリックします。  
  
     **\[継承ピッカー\]** ダイアログ ボックスが表示されます。  
  
4.  **\[コンポーネント名\]** の **\[ctlClock\]** をダブルクリックします。  
  
5.  ソリューション エクスプローラーで、現在のプロジェクトを最後まで参照します。  
  
    > [!NOTE]
    >  現在のプロジェクトに **ctlAlarmClock.vb** という名前のファイルが追加されています。  
  
### アラーム プロパティの追加  
 複合コントロールにプロパティを追加する場合と同じ方法で、継承コントロールにプロパティを追加できます。  ここでは、プロパティ宣言の構文を使用してコントロールに 2 つのプロパティを追加します。`AlarmTime` プロパティは、アラームを鳴らす日付と時刻の値を格納します。`AlarmSet` プロパティは、アラームが設定されているかどうかを示します。  
  
##### 複合コントロールにプロパティを追加するには  
  
1.  ソリューション エクスプローラーで、**\[ctlAlarmClock\]** を右クリックし、**\[コードの表示\]** をクリックします。  
  
2.  `Public Class ctlAlarmClock` として表示されている ctlAlarmClock コントロールのクラス宣言を探します。  クラス宣言に次のコードを挿入します。  
  
     \[Visual Basic\]  
  
    ```  
    Private dteAlarmTime As Date  
    Private blnAlarmSet As Boolean  
    ' These properties will be declared as Public to allow future   
    ' developers to access them.  
    Public Property AlarmTime() As Date  
        Get  
            Return dteAlarmTime  
        End Get  
        Set(ByVal value as Date)  
            dteAlarmTime = value  
        End Set  
    End Property  
    Public Property AlarmSet() As Boolean  
        Get  
            Return blnAlarmSet  
        End Get  
        Set(ByVal value as Boolean)  
            blnAlarmSet = value  
        End Set  
    End Property  
    ```  
  
### コントロールのグラフィカル インターフェイスへの追加  
 継承したコントロールには、継承元のコントロールと同じビジュアル インターフェイスがあります。  継承コントロールには親コントロールと同じ内在コントロールがありますが、内在コントロールのプロパティは特に公開されない限り使用できません。  継承した複合コントロールのグラフィカル インターフェイスも、他の複合コントロールと同じように拡張できます。  引き続き、アラーム クロックのビジュアル インターフェイスに、アラームが鳴ったときに点滅するラベル コントロールを追加します。  
  
##### ラベル コントロールを追加するには  
  
1.  ソリューション エクスプローラーで、**\[ctlAlarmClock\]** を右クリックし、**\[デザイナーの表示\]** をクリックします。  
  
     `ctlAlarmClock` のデザイナーがメイン ウィンドウに表示されます。  
  
2.  `lblDisplay` \(コントロールの表示部分\) をクリックし、\[プロパティ\] ウィンドウを表示します。  
  
    > [!NOTE]
    >  すべてのプロパティが表示されていますが、淡色表示になっています。  つまり、これらのプロパティは `lblDisplay` に対してネイティブであり、\[プロパティ\] ウィンドウでは変更もアクセスもできません。  既定では、複合コントロールに含まれているコントロールは `Private` であり、どのような方法によってもプロパティにアクセスできません。  
  
    > [!NOTE]
    >  今後複合コントロールを使用するユーザーがその内部のコントロールにアクセスできるようにするには、内部のコントロールを `Public` または `Protected` として宣言します。  これにより、適切なコードを使用して、複合コントロールに含まれるコントロールのプロパティを設定したり変更したりできるようになります。  
  
3.  複合コントロールに <xref:System.Windows.Forms.Label> コントロールを追加します。  
  
4.  マウスを使用して、<xref:System.Windows.Forms.Label> コントロールを表示ボックスのすぐ下にドラッグします。  プロパティ ウィンドウで、次のプロパティを設定します。  
  
    |プロパティ|設定|  
    |-----------|--------|  
    |**名前**|`lblAlarm`|  
    |**テキスト**|Alarm\!|  
    |**TextAlign**|`MiddleCenter`|  
    |**Visible**|`False`|  
  
### アラーム機能の追加  
 前の手順では、複合コントロールでアラーム機能を有効にするためのプロパティおよびコントロールを追加しました。  この手順では、現在の時刻をアラーム設定時刻と比較して、一致した場合にはアラームを鳴らしてラベルを点滅させるコードを追加します。  `ctlClock` の `Timer1_Tick` メソッドをオーバーライドしてコードを追加することにより、`ctlClock` の固有の機能をすべて保持しながら `ctlAlarmClock` の機能を拡張できます。  
  
##### ctlClock の Timer1\_Tick メソッドをオーバーライドするには  
  
1.  ソリューション エクスプローラーで **ctlAlarmClock.vb** を右クリックし、**\[コードの表示\]** をクリックします。  
  
2.  `Private blnAlarmSet As Boolean` ステートメントを探します。  このステートメントの直後に、次のステートメントを追加します。  
  
     \[Visual Basic\]  
  
    ```  
    Dim blnColorTicker as Boolean  
    ```  
  
3.  ページの下部にある `End Class` ステートメントを探します。  `End Class` ステートメントの直前に、次のコードを追加します。  
  
     \[Visual Basic\]  
  
    ```  
    Protected Overrides Sub Timer1_Tick(ByVal sender As Object, ByVal e _  
        As System.EventArgs)  
        ' Calls the Timer1_Tick method of ctlClock.  
        MyBase.Timer1_Tick(sender, e)  
        ' Checks to see if the Alarm is set.  
        If AlarmSet = False Then  
            Exit Sub  
        End If  
        ' If the date, hour, and minute of the alarm time are the same as  
        ' now, flash and beep an alarm.   
        If AlarmTime.Date = Now.Date And AlarmTime.Hour = Now.Hour And _  
            AlarmTime.Minute = Now.Minute Then  
            ' Sounds an audible beep.  
            Beep()  
            ' Sets lblAlarmVisible to True, and changes the background color based on the   
            ' value of blnColorTicker. The background color of the label will   
            ' flash once per tick of the clock.  
            lblAlarm.Visible = True  
            If blnColorTicker = False Then  
                lblAlarm.BackColor = Color.PeachPuff  
                blnColorTicker = True  
            Else  
                lblAlarm.BackColor = Color.Plum  
                blnColorTicker = False  
            End If  
        Else  
            ' Once the alarm has sounded for a minute, the label is made   
            ' invisible again.  
            lblAlarm.Visible = False  
        End If  
    End Sub  
    ```  
  
     このコードを追加することで、いくつかのタスクが実行されます。  `Overrides` ステートメントは、基本コントロールから継承されたメソッドの代わりに、このメソッドを使用するようにコントロールに指示します。  このメソッドが呼び出されると、メソッドは `MyBase.Timer1_Tick` ステートメントを呼び出すことにより、オーバーライドするメソッドを呼び出します。その結果、元のコントロールに含まれるすべての機能がこのコントロールに継承されます。  メソッドは次に追加のコードを実行してアラーム機能を組み込みます。  アラームが発生すると、点滅するラベル コントロールが表示され、ビープ音が聞こえます。  
  
    > [!NOTE]
    >  オーバーライドしているのは継承したイベント ハンドラーであるため、`Handles` キーワードでイベントを指定する必要はありません。  イベントは既にフックされています。  オーバーライドしているのはハンドラーの実装です。  
  
     これで、アラーム付き時計はほぼ完成です。  後は、アラームを止める手段を実装するだけです。  これを行うには、`lblAlarm_Click` メソッドにコードを追加します。  
  
##### アラームを止める手段を実装するには  
  
1.  ソリューション エクスプローラーで **ctlAlarmClock.vb** を右クリックし、**\[デザイナーの表示\]** をクリックします。  
  
2.  デザイナーで **lblAlarm** をダブルクリックします。  **コード エディター**が開き、`Private Sub lblAlarm_Click` 行が表示されます。  
  
3.  このメソッドを次のコードのように変更します。  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub lblAlarm_Click(ByVal sender As Object, ByVal e As _  
     System.EventArgs) Handles lblAlarm.Click  
        ' Turns off the alarm.  
        AlarmSet = False  
        ' Hides the flashing label.  
        lblAlarm.Visible = False  
    End Sub  
    ```  
  
4.  **\[ファイル\]** メニューの **\[すべてを保存\]** をクリックして、プロジェクトを保存します。  
  
### フォームでの継承コントロールの使用  
 継承コントロールは、基本クラスである `ctlClock` のテストと同様の方法でテストできます。F5 キーを押してプロジェクトをビルドし、**ユーザー コントロール テスト コンテナー**でコントロールを実行します。  詳細については、「[方法 : UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。  
  
 コントロールを使用できるようにするには、フォーム上でコントロールをホストする必要があります。  標準複合コントロールと同様に、継承複合コントロールはスタンドアロン型ではないため、フォームまたは他のコンテナーでホストする必要があります。  `ctlAlarmClock` は機能が拡張されているため、テストにも追加のコードが必要です。  次の手順では、`ctlAlarmClock` の機能をテストするための簡単なプログラムを記述します。  `ctlAlarmClock` の `AlarmTime` プロパティを設定および表示するコードを作成し、固有の機能をテストします。  
  
##### コントロールをビルドしてテスト フォームに追加するには  
  
1.  ソリューション エクスプローラーで、**\[ctlClockLib\]** を右クリックし、**\[ビルド\]** をクリックします。  
  
2.  **\[ファイル\]** メニューの **\[追加\]** をポイントし、**\[新しいプロジェクト\]** をクリックします。  
  
3.  ソリューションに新しい **Windows アプリケーション** プロジェクトを追加し、「`Test`」という名前を付けます。  
  
     **Test** プロジェクトがソリューション エクスプローラーに追加されます。  
  
4.  ソリューション エクスプローラーで、\[`Test`\] プロジェクト ノードを右クリックし、**\[参照の追加\]** をクリックして **\[参照の追加\]** ダイアログ ボックスを表示します。  
  
5.  **\[プロジェクト\]** タブをクリックします。  **ctlClockLib** プロジェクトが **\[プロジェクト名\]** の下に表示されます。  **\[ctlClockLib\]** をダブルクリックして、テスト プロジェクトに参照を追加します。  
  
6.  ソリューション エクスプローラーで、**Test** を右クリックし、**\[ビルド\]** をクリックします。  
  
7.  **ツールボックス**で、**\[ctlClockLib コンポーネント\]** ノードを展開します。  
  
8.  **\[ctlAlarmClock\]** をダブルクリックして、`ctlAlarmClock` のインスタンスをフォームに追加します。  
  
9. **ツールボックス**で、**\[DateTimePicker\]** を検索してダブルクリックし、<xref:System.Windows.Forms.DateTimePicker> コントロールをフォームに追加します。また、**\[Label\]** をダブルクリックして <xref:System.Windows.Forms.Label> コントロールを追加します。  
  
10. マウスを使用して、フォーム上で各コントロールを使いやすい位置に移動します。  
  
11. コントロールのプロパティを次のように設定します。  
  
    |Control|プロパティ|値|  
    |-------------|-----------|-------|  
    |`label1`|**テキスト**|`(空白)`|  
    ||**名前**|`lblTest`|  
    |`dateTimePicker1`|**名前**|`dtpTest`|  
    ||**書式**|<xref:System.Windows.Forms.DateTimePickerFormat>|  
  
12. デザイナーで、**\[dtpTest\]** をダブルクリックします。  
  
     **コード エディター**が開き、`Private Sub dtpTest_ValueChanged` が表示されます。  
  
13. コードを次のように変更します。  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub dtpTest_ValueChanged(ByVal sender As Object, ByVal e As _  
        System.EventArgs) Handles dtpTest.ValueChanged  
        ctlAlarmClock1.AlarmTime = dtpTest.Value  
        ctlAlarmClock1.AlarmSet = True  
        lblTest.Text = "Alarm Time is " & Format(ctlAlarmClock1.AlarmTime, _  
            "hh:mm")  
    End Sub  
    ```  
  
14. ソリューション エクスプローラーで、**Test** を右クリックし、**\[スタートアップ プロジェクトに設定\]** をクリックします。  
  
15. **\[デバッグ\]** メニューの **\[デバッグ開始\]** をクリックします。  
  
     テスト プログラムが起動します。  `ctlAlarmClock` コントロールの現在時刻が更新され、<xref:System.Windows.Forms.DateTimePicker> コントロールに開始時刻が表示されます。  
  
16. <xref:System.Windows.Forms.DateTimePicker> で分が表示されている部分をクリックします。  
  
17. キーボードを使用して、`ctlAlarmClock` によって表示されている現在の時刻より 1 分後の値を設定します。  
  
     アラーム設定時刻は `lblTest` に表示されます。  表示時刻がアラームの設定時刻になるまで待ちます。  表示時刻がアラーム設定時刻になると、ビープ音が鳴り、`lblAlarm` が点滅します。  
  
18. `lblAlarm` をクリックしてアラームを止めます。  その後で、アラームを再び設定できます。  
  
     このチュートリアルでは、多数の重要な概念を扱いました。  複合コントロール コンテナーにコントロールやコンポーネントを組み込んで複合コントロールを作成する方法を学びました。  また、コントロールにプロパティを追加する方法や、カスタム機能を実装するコードを記述する方法も学びました。  最後のセクションでは、継承によって特定の複合コントロールの機能を拡張し、オーバーライドによりホストのメソッドの機能を変更する方法を学びました。  
  
## 参照  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [方法 : 複合コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)   
 [方法: \[ツールボックス アイテムの選択\] ダイアログ ボックスにコントロールを表示する](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)   
 [Component Authoring Walkthroughs](../Topic/Component%20Authoring%20Walkthroughs.md)