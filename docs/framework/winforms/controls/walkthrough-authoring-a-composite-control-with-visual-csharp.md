---
title: "チュートリアル : Visual C# による複合コントロールの作成 | Microsoft Docs"
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
  - "カスタム コントロール [C#]"
  - "カスタム コントロール [Windows フォーム], 作成"
  - "ユーザー コントロール [C#]"
  - "ユーザー コントロール [Windows フォーム], 作成 (Visual C# を使用した)"
  - "UserControl クラス, チュートリアル"
ms.assetid: f88481a8-c746-4a36-9479-374ce5f2e91f
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# チュートリアル : Visual C# による複合コントロールの作成
複合コントロールは、カスタム グラフィカル インターフェイスの作成と再利用のための手段を提供します。  複合コントロールは、基本的には表示できる形式を持つコンポーネントです。  そのため、ユーザー コントロールは、1 つ以上の Windows フォーム コントロール、コンポーネント、またはコードのブロックから構成でき、ユーザー入力を検査したり、表示プロパティを変更したり、作成者によって要求されるその他のタスクを実行したりすることで機能を拡張できます。  複合コントロールは、他のコントロールと同じ方法で Windows フォームに配置できます。  このチュートリアルの前半では、`ctlClock` という名前の単純な複合コントロールを作成します。  後半では、継承によって `ctlClock` の機能を拡張します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## プロジェクトの作成  
 新しいプロジェクトを作成するときには、その名前を指定することにより、ルート名前空間、アセンブリ名、およびプロジェクト名を設定し、既定のコンポーネントが正しい名前空間に含まれるようにします。  
  
#### ctlClockLib コントロール ライブラリおよび ctlClock コントロールを作成するには  
  
1.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックして **\[新しいプロジェクト\]** ダイアログ ボックスを表示します。  
  
2.  [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] プロジェクトの一覧の **\[Windows フォーム コントロール ライブラリ\]** プロジェクト テンプレートをクリックし、**\[プロジェクト名\]** ボックスに「`ctlClockLib`」と入力し、**\[OK\]** をクリックします。  
  
     プロジェクト名 `ctlClockLib` は、既定でルート名前空間にも割り当てられます。  ルート名前空間は、アセンブリ内のコンポーネント名の修飾に使用されます。  たとえば、`ctlClock` という名前のコンポーネントが 2 つのアセンブリに含まれる場合は、`ctlClockLib.ctlClock` という形で目的の `ctlClock` コンポーネントを指定できます。  
  
3.  ソリューション エクスプローラーで、**UserControl1.cs** を右クリックし、**\[名前の変更\]** をクリックします。  ファイル名を「`ctlClock.cs`」に変更します。  コード要素 "UserControl1" へのすべての参照の名前を変更するかどうかを確認するダイアログ ボックスが表示されたら、**\[はい\]** をクリックします。  
  
    > [!NOTE]
    >  既定では、複合コントロールはシステムによって提供される <xref:System.Windows.Forms.UserControl> クラスを継承します。  <xref:System.Windows.Forms.UserControl> クラスは、すべての複合コントロールに必要な機能を提供し、標準のメソッドおよびプロパティを実装します。  
  
4.  **\[ファイル\]** メニューの **\[すべてを保存\]** をクリックして、プロジェクトを保存します。  
  
## 複合コントロールへの Windows コントロールおよびコンポーネントの追加  
 ビジュアル インターフェイスは、複合コントロールの基本的な部分です。  このビジュアル インターフェイスは、デザイナー画面に 1 つ以上の Windows コントロールを追加することによって実装されます。  次の例では、複合コントロールに Windows コントロールを取り込んで、機能を実装するコードを記述します。  
  
#### 複合コントロールに Label と Timer を追加するには  
  
1.  ソリューション エクスプローラーで **ctlClock.cs** を右クリックし、**\[デザイナーの表示\]** をクリックします。  
  
2.  **ツールボックス**の **\[コモン コントロール\]** ノードを展開し、**\[Label\]** をダブルクリックします。  
  
     `label1` という名前の <xref:System.Windows.Forms.Label> がデザイナー画面のコントロールに追加されます。  
  
3.  デザイナーで、**\[label1\]** をクリックします。  プロパティ ウィンドウで、次のプロパティを設定します。  
  
    |プロパティ|変更後の値|  
    |-----------|-----------|  
    |**名前**|`lblDisplay`|  
    |**テキスト**|`(空白)`|  
    |**TextAlign**|`MiddleCenter`|  
    |**Font.Size**|`14`|  
  
4.  **ツールボックス**の **\[コンポーネント\]** ノードを展開し、**\[Timer\]** をダブルクリックします。  
  
     <xref:System.Windows.Forms.Timer> はコンポーネントであるため、実行時には表示できる形式を持ちません。  このため、デザイナー画面にはコントロールと共には表示されず、**コンポーネント デザイナー** \(デザイナー画面の下部にあるトレイ\) に表示されます。  
  
5.  **コンポーネント デザイナー**で、**\[Timer1\]** をクリックし、<xref:System.Windows.Forms.Timer.Interval%2A> プロパティを `1000`、<xref:System.Windows.Forms.Timer.Enabled%2A> プロパティを `true` に設定します。  
  
     <xref:System.Windows.Forms.Timer.Interval%2A> プロパティは、<xref:System.Windows.Forms.Timer> コンポーネントが時を刻む頻度を制御します。  `timer1` が時を刻むたびに、`timer1_Tick` イベントのコードが実行されます。  このプロパティは、タイマーが何ミリ秒ごとに時を刻むかを表しています。  
  
6.  **コンポーネント デザイナー**で、**\[Timer1\]** をダブルクリックして、`ctlClock` の `timer1_Tick` イベントに移動します。  
  
7.  コードを次のコード サンプルのように変更します。  アクセス修飾子を必ず `private` から `protected` に変更してください。  
  
     \[C\#\]  
  
    ```  
    protected void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Causes the label to display the current time.  
        lblDisplay.Text = DateTime.Now.ToLongTimeString();   
    }  
    ```  
  
     このコードは、現在の時刻を `lblDisplay` に表示します。  `timer1` の間隔は 1000 に設定されているため、このイベントは `1000` ミリ秒ごとに発生します。したがって、現在の時刻は 1 秒ごとに更新されます。  
  
8.  `virtual` キーワードを使用して、メソッドをオーバーライドできるように変更します。  詳細については、後の「ユーザー コントロールからの継承」を参照してください。  
  
    ```  
    protected virtual void timer1_Tick(object sender, System.EventArgs e)  
    ```  
  
9. **\[ファイル\]** メニューの **\[すべてを保存\]** をクリックして、プロジェクトを保存します。  
  
## 複合コントロールへのプロパティの追加  
 現在、クロック コントロールは、それぞれが固有のプロパティ セットを持つ <xref:System.Windows.Forms.Label> コントロールと <xref:System.Windows.Forms.Timer> コンポーネントをカプセル化しています。  各コントロールのプロパティは、コントロールの後続のユーザーからはアクセスできませんが、適切なコード ブロックを作成することによってカスタム プロパティを作成および公開できます。  次の手順では、ユーザーが背景とテキストの色を変更できるようにするプロパティをコントロールに追加します。  
  
#### 複合コントロールにプロパティを追加するには  
  
1.  ソリューション エクスプローラーで、**ctlClock.cs** を右クリックし、**\[コードの表示\]** をクリックします。  
  
     コントロールの**コード エディター**が表示されます。  
  
2.  `public partial class ctlClock` ステートメントを探します。  左中かっこ \(`{)` の下に次のコードを入力します。  
  
     \[C\#\]  
  
    ```  
    private Color colFColor;  
    private Color colBColor;  
    ```  
  
     これらのステートメントは、作成するプロパティの値を格納するために使用するプライベート変数を作成します。  
  
3.  手順 2. の変数宣言の下に次のコードを入力します。  
  
     \[C\#\]  
  
    ```  
    // Declares the name and type of the property.  
    public Color ClockBackColor  
    {  
        // Retrieves the value of the private variable colBColor.  
        get  
        {  
            return colBColor;  
        }  
        // Stores the selected value in the private variable colBColor, and   
        // updates the background color of the label control lblDisplay.  
        set  
        {  
            colBColor = value;  
            lblDisplay.BackColor = colBColor;     
        }  
    }  
    // Provides a similar set of instructions for the foreground color.  
    public Color ClockForeColor  
    {  
        get  
        {  
            return colFColor;  
        }  
        set  
        {  
            colFColor = value;  
            lblDisplay.ForeColor = colFColor;  
        }  
    }  
    ```  
  
     上記のコードは、このコントロールを今後使用するユーザーが `ClockForeColor` および `ClockBackColor` という 2 つのカスタム プロパティを使用できるようにします。  `get` ステートメントと `set` ステートメントは、プロパティに適切な機能を実装するコードと共に、プロパティ値の格納と取得の機能を提供します。  
  
4.  **\[ファイル\]** メニューの **\[すべてを保存\]** をクリックして、プロジェクトを保存します。  
  
## コントロールのテスト  
 コントロールはスタンドアロン アプリケーションではないため、コンテナーでホストする必要があります。  コントロールの実行時の動作をテストし、**ユーザー コントロール テスト コンテナー**でそのプロパティを実行します。  詳細については、「[方法 : UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。  
  
#### コントロールをテストするには  
  
1.  F5 キーを押してプロジェクトをビルドし、**ユーザー コントロール テスト コンテナー**でコントロールを実行します。  
  
2.  テスト コンテナーのプロパティ グリッドで、`ClockBackColor` プロパティを検索し、プロパティを選択してカラー パレットを表示します。  
  
3.  任意の色をクリックして選択します。  
  
     コントロールの背景色が、選択した色に変更されます。  
  
4.  同様なイベントのシーケンスを使用して、`ClockForeColor` プロパティが予想どおりに機能することを確認します。  
  
     このセクションと前のセクションでは、コンポーネントと Windows コントロールをコードと結合し、複合コントロールの形式にパッケージ化してカスタム機能を提供する方法を説明しました。  複合コントロールのプロパティを公開し、完了後にコントロールをテストする方法を学びました。  次のセクションでは、`ctlClock` をベースとして継承した複合コントロールを構築する方法を学びます。  
  
## 複合コントロールからの継承  
 前のセクションでは、再利用可能な複合コントロールに Windows コントロール、コンポーネント、およびコードを組み込む方法を学びました。  この複合コントロールをベースにして、他のコントロールを作成できます。  基本クラスからクラスを派生するプロセスは*継承*と呼ばれます。  このセクションでは、`ctlAlarmClock` という名前の複合コントロールを作成します。  このコントロールは、親コントロールである `ctlClock` から派生します。  ここでは、親のメソッドをオーバーライドし、新しいメソッドおよびプロパティを追加することにより、`ctlClock` の機能を拡張する方法を学びます。  
  
 継承コントロールの作成の最初の手順は、親コントロールからの派生です。  これにより、親コントロールのプロパティ、メソッド、およびグラフィカル特性をすべて持つ新しいコントロールが作成されます。このコントロールに基づいて、新しい機能を追加したり機能を変更したりできます。  
  
#### 継承コントロールを作成するには  
  
1.  ソリューション エクスプローラーで、**\[ctlClockLib\]** を右クリックします。**\[追加\]** をポイントし、**\[ユーザー コントロール\]** をクリックします。  
  
     **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
2.  **\[継承されたユーザー コントロール\]** テンプレートを選択します。  
  
3.  **\[ファイル名\]** ボックスに「`ctlAlarmClock.cs`」と入力し、**\[追加\]** をクリックします。  
  
     **\[継承ピッカー\]** ダイアログ ボックスが表示されます。  
  
4.  **\[コンポーネント名\]** の **\[ctlClock\]** をダブルクリックします。  
  
5.  ソリューション エクスプローラーで、現在のプロジェクトを最後まで参照します。  
  
    > [!NOTE]
    >  現在のプロジェクトに **ctlAlarmClock.cs** という名前のファイルが追加されています。  
  
### アラーム プロパティの追加  
 複合コントロールにプロパティを追加する場合と同じ方法で、継承コントロールにプロパティを追加できます。  ここでは、プロパティ宣言の構文を使用してコントロールに 2 つのプロパティを追加します。`AlarmTime` プロパティは、アラームを鳴らす日付と時刻の値を格納します。`AlarmSet` プロパティは、アラームが設定されているかどうかを示します。  
  
##### 複合コントロールにプロパティを追加するには  
  
1.  ソリューション エクスプローラーで、**\[ctlAlarmClock\]** を右クリックし、**\[コードの表示\]** をクリックします。  
  
2.  `public class` ステートメントを探します。  コントロールが `ctlClockLib.ctlClock` から継承される点に注意してください。  左中かっこ \(`{)` ステートメントの下に次のコードを入力します。  
  
     \[C\#\]  
  
    ```  
    private DateTime dteAlarmTime;  
    private bool blnAlarmSet;  
    // These properties will be declared as public to allow future   
    // developers to access them.  
    public DateTime AlarmTime  
    {  
        get  
        {  
            return dteAlarmTime;  
        }  
        set  
        {  
            dteAlarmTime = value;  
        }  
    }  
    public bool AlarmSet  
    {  
        get  
        {  
            return blnAlarmSet;  
        }  
        set  
        {  
            blnAlarmSet = value;  
        }  
    }  
    ```  
  
### コントロールのグラフィカル インターフェイスへの追加  
 継承したコントロールには、継承元のコントロールと同じビジュアル インターフェイスがあります。  継承コントロールには親コントロールと同じ内在コントロールがありますが、内在コントロールのプロパティは特に公開されない限り使用できません。  継承した複合コントロールのグラフィカル インターフェイスも、他の複合コントロールと同じように拡張できます。  引き続き、アラーム クロックのビジュアル インターフェイスに、アラームが鳴ったときに点滅するラベル コントロールを追加します。  
  
##### ラベル コントロールを追加するには  
  
1.  ソリューション エクスプローラーで、**\[ctlAlarmClock\]** を右クリックし、**\[デザイナーの表示\]** をクリックします。  
  
     `ctlAlarmClock` のデザイナーがメイン ウィンドウに表示されます。  
  
2.  コントロールの表示部分をクリックし、\[プロパティ\] ウィンドウを表示します。  
  
    > [!NOTE]
    >  すべてのプロパティが表示されていますが、淡色表示になっています。  つまり、これらのプロパティは `lblDisplay` に対してネイティブであり、\[プロパティ\] ウィンドウでは変更もアクセスもできません。  既定では、複合コントロールに含まれているコントロールは `private` であり、どのような方法によってもプロパティにアクセスできません。  
  
    > [!NOTE]
    >  複合コントロールを今後使用するユーザーがその内部のコントロールにアクセスできるようにするには、内部のコントロールを `public` または `protected` として宣言します。  これにより、適切なコードを使用して、複合コントロールに含まれるコントロールのプロパティを設定したり変更したりできるようになります。  
  
3.  複合コントロールに <xref:System.Windows.Forms.Label> コントロールを追加します。  
  
4.  マウスを使用して、<xref:System.Windows.Forms.Label> コントロールを表示ボックスのすぐ下にドラッグします。  プロパティ ウィンドウで、次のプロパティを設定します。  
  
    |プロパティ|設定|  
    |-----------|--------|  
    |**名前**|`lblAlarm`|  
    |**テキスト**|Alarm\!|  
    |**TextAlign**|`MiddleCenter`|  
    |**Visible**|`false`|  
  
### アラーム機能の追加  
 前の手順では、複合コントロールでアラーム機能を有効にするためのプロパティおよびコントロールを追加しました。  この手順では、現在の時刻とアラームの時刻を比較し、一致した場合は、アラームを点滅させるコードを追加します。  `ctlClock` の `timer1_Tick` メソッドをオーバーライドしてコードを追加することにより、`ctlClock` の固有の機能をすべて保持しながら `ctlAlarmClock` の機能を拡張できます。  
  
##### ctlClock の timer1\_Tick メソッドをオーバーライドするには  
  
1.  **コード エディター**で、`private bool blnAlarmSet;` ステートメントを検索します。  このステートメントの直後に、次のステートメントを追加します。  
  
     \[C\#\]  
  
    ```  
    private bool blnColorTicker;  
    ```  
  
2.  **コード エディター**で、クラスの末尾にある右中かっこ \(`})` を検索します。  中かっこの直前に、次のコードを追加します。  
  
     \[C\#\]  
  
    ```  
    protected override void timer1_Tick(object sender, System.EventArgs e)  
    {  
        // Calls the Timer1_Tick method of ctlClock.  
        base.timer1_Tick(sender, e);  
        // Checks to see if the alarm is set.  
        if (AlarmSet == false)  
            return;  
        else  
            // If the date, hour, and minute of the alarm time are the same as  
            // the current time, flash an alarm.   
        {  
            if (AlarmTime.Date == DateTime.Now.Date && AlarmTime.Hour ==   
                DateTime.Now.Hour && AlarmTime.Minute == DateTime.Now.Minute)  
            {  
                // Sets lblAlarmVisible to true, and changes the background color based on  
                // the value of blnColorTicker. The background color of the label   
                // will flash once per tick of the clock.  
                lblAlarm.Visible = true;  
                if (blnColorTicker == false)   
                {  
                    lblAlarm.BackColor = Color.Red;  
                    blnColorTicker = true;  
                }  
                else  
                {  
                    lblAlarm.BackColor = Color.Blue;  
                    blnColorTicker = false;  
                }  
            }  
            else  
            {  
                // Once the alarm has sounded for a minute, the label is made   
                // invisible again.  
                lblAlarm.Visible = false;  
            }  
        }  
    }  
    ```  
  
     このコードを追加することで、いくつかのタスクが実行されます。  `override` ステートメントは、基本コントロールから継承されたメソッドの代わりに、このメソッドを使用するようにコントロールに指示します。  このメソッドが呼び出されると、メソッドは `base.timer1_Tick` ステートメントを呼び出すことにより、オーバーライドするメソッドを呼び出します。その結果、元のコントロールに含まれるすべての機能がこのコントロールに継承されます。  メソッドは次に追加のコードを実行してアラーム機能を組み込みます。  アラームが発生すると、点滅するラベル コントロールが表示されます。  
  
     これで、アラーム付き時計はほぼ完成です。  後は、アラームを止める手段を実装するだけです。  これを行うには、`lblAlarm_Click` メソッドにコードを追加します。  
  
##### アラームを止める手段を実装するには  
  
1.  ソリューション エクスプローラーで、**ctlAlarmClock.cs** を右クリックし、**\[デザイナーの表示\]** をクリックします。  
  
     デザイナーが表示されます。  
  
2.  コントロールにボタンを追加します。  ボタンのプロパティを次のように設定します。  
  
    |プロパティ|値|  
    |-----------|-------|  
    |**名前**|`btnAlarmOff`|  
    |**テキスト**|Disable Alarm|  
  
3.  デザイナーで、**\[btnAlarmOff\]** をダブルクリックします。  
  
     **コード エディター**が開き、`private void btnAlarmOff_Click` 行が表示されます。  
  
4.  このメソッドを次のコードのように変更します。  
  
     \[C\#\]  
  
    ```  
    private void btnAlarmOff_Click(object sender, System.EventArgs e)  
    {  
        // Turns off the alarm.  
        AlarmSet = false;  
        // Hides the flashing label.  
        lblAlarm.Visible = false;  
    }  
    ```  
  
5.  **\[ファイル\]** メニューの **\[すべてを保存\]** をクリックして、プロジェクトを保存します。  
  
### フォームでの継承コントロールの使用  
 継承コントロールは、基本クラスである `ctlClock` のテストと同様の方法でテストできます。F5 キーを押してプロジェクトをビルドし、**ユーザー コントロール テスト コンテナー**でコントロールを実行します。  詳細については、「[方法 : UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。  
  
 コントロールを使用できるようにするには、フォーム上でコントロールをホストする必要があります。  標準複合コントロールと同様に、継承複合コントロールはスタンドアロン型ではないため、フォームまたは他のコンテナーでホストする必要があります。  `ctlAlarmClock` は機能が拡張されているため、テストにも追加のコードが必要です。  次の手順では、`ctlAlarmClock` の機能をテストするための簡単なプログラムを記述します。  `ctlAlarmClock` の `AlarmTime` プロパティを設定および表示するコードを作成し、固有の機能をテストします。  
  
##### コントロールをビルドしてテスト フォームに追加するには  
  
1.  ソリューション エクスプローラーで、**\[ctlClockLib\]** を右クリックし、**\[ビルド\]** をクリックします。  
  
2.  ソリューションに新しい **Windows アプリケーション** プロジェクトを追加し、「`Test`」という名前を付けます。  
  
3.  ソリューション エクスプローラーで、テスト プロジェクトの **\[参照設定\]** ノードを右クリックします。  **\[参照の追加\]** をクリックして **\[参照の追加\]** ダイアログ ボックスを表示します。  **\[プロジェクト\]** タブをクリックします。  `ctlClockLib` プロジェクトが **\[プロジェクト名\]** の下に表示されます。  プロジェクトをダブルクリックしてテスト プロジェクトへの参照を追加します。  
  
4.  ソリューション エクスプローラーで、**Test** を右クリックし、**\[ビルド\]** をクリックします。  
  
5.  **ツールボックス**で、**\[ctlClockLib コンポーネント\]** ノードを展開します。  
  
6.  **\[ctlAlarmClock\]** をダブルクリックして、`ctlAlarmClock` をフォームにコピーします。  
  
7.  **ツールボックス**で、**\[DateTimePicker\]** を検索してダブルクリックし、<xref:System.Windows.Forms.DateTimePicker> コントロールをフォームに追加します。また、**\[Label\]** をダブルクリックして <xref:System.Windows.Forms.Label> コントロールを追加します。  
  
8.  マウスを使用して、フォーム上で各コントロールを使いやすい位置に移動します。  
  
9. コントロールのプロパティを次のように設定します。  
  
    |Control|プロパティ|値|  
    |-------------|-----------|-------|  
    |`label1`|**テキスト**|`(空白)`|  
    ||**名前**|`lblTest`|  
    |`dateTimePicker1`|**名前**|`dtpTest`|  
    ||**書式**|<xref:System.Windows.Forms.DateTimePickerFormat>|  
  
10. デザイナーで、**\[dtpTest\]** をダブルクリックします。  
  
     **コード エディター**が開き、`private void dtpTest_ValueChanged` が表示されます。  
  
11. コードを次のように変更します。  
  
     \[C\#\]  
  
    ```  
    private void dtpTest_ValueChanged(object sender, System.EventArgs e)  
    {  
        ctlAlarmClock1.AlarmTime = dtpTest.Value;  
        ctlAlarmClock1.AlarmSet = true;  
        lblTest.Text = "Alarm Time is " +  
            ctlAlarmClock1.AlarmTime.ToShortTimeString();  
    }  
    ```  
  
12. ソリューション エクスプローラーで、**Test** を右クリックし、**\[スタートアップ プロジェクトに設定\]** をクリックします。  
  
13. **\[デバッグ\]** メニューの **\[デバッグ開始\]** をクリックします。  
  
     テスト プログラムが起動します。  `ctlAlarmClock` コントロールの現在時刻が更新され、<xref:System.Windows.Forms.DateTimePicker> コントロールに開始時刻が表示されます。  
  
14. <xref:System.Windows.Forms.DateTimePicker> で分が表示されている部分をクリックします。  
  
15. キーボードを使用して、`ctlAlarmClock` によって表示されている現在の時刻より 1 分後の値を設定します。  
  
     アラーム設定時刻は `lblTest` に表示されます。  表示時刻がアラームの設定時刻になるまで待ちます。  表示時刻がアラームの設定時刻になったときに、`lblAlarm` が点滅します。  
  
16. `btnAlarmOff` をクリックしてアラームを止めます。  その後で、アラームを再び設定できます。  
  
     このチュートリアルでは、多数の重要な概念を扱いました。  複合コントロール コンテナーにコントロールやコンポーネントを組み込んで複合コントロールを作成する方法を学びました。  また、コントロールにプロパティを追加する方法や、カスタム機能を実装するコードを記述する方法も学びました。  最後のセクションでは、継承によって特定の複合コントロールの機能を拡張し、オーバーライドによりホストのメソッドの機能を変更する方法を学びました。  
  
## 参照  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)   
 [コンポーネントによるプログラミング](../Topic/Programming%20with%20Components.md)   
 [Component Authoring Walkthroughs](../Topic/Component%20Authoring%20Walkthroughs.md)   
 [方法: \[ツールボックス アイテムの選択\] ダイアログ ボックスにコントロールを表示する](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)   
 [チュートリアル : Visual C\# による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)