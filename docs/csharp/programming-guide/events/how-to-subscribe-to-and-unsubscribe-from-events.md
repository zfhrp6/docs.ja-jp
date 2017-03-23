---
title: "方法 : イベント サブスクリプションとサブスクリプションの解除 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "コード エディター, イベント ハンドラー"
  - "イベント ハンドラー [C#], 作成"
  - "イベント [C#], 作成 (IDE を使用して)"
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 方法 : イベント サブスクリプションとサブスクリプションの解除 (C# プログラミング ガイド)
イベントの発生時に呼び出されるカスタム コードを作成するときは、別のクラスによって発行されたイベントをサブスクライブします。  たとえば、ユーザーのボタン クリックでアプリケーションに何らかの処理を実行させるには、ボタンの `click` イベントをサブスクライブします。  
  
### Visual Studio IDE を使用してイベントをサブスクライブするには  
  
1.  **\[プロパティ\]** ウィンドウが表示されていない場合は、**\[デザイン\]** ビューで、イベント ハンドラーを作成するフォームまたはコントロールを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  **\[プロパティ\]** ウィンドウの上部にある **\[イベント\]** アイコンをクリックします。  
  
3.  `Load` イベントなど、作成するイベントをダブルクリックします。  
  
     [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] により空のイベント ハンドラー メソッドが作成され、コードに追加されます。  **\[コード\]** ビューを使用して手動でコードを追加することもできます。  たとえば次のコード行では、`Form` クラスが `Load` イベントを発生させたときに呼び出されるイベント ハンドラー メソッドを宣言しています。  
  
     [!code-cs[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     プロジェクトの Form1.Designer.cs ファイルの `InitializeComponent` メソッド内に、イベントをサブスクライブする必要があるコード行も自動生成されます。  次のようになります。  
  
    ```  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### プログラムを使用してイベントをサブスクライブするには  
  
1.  シグネチャがイベントのデリゲート シグネチャと一致するイベント ハンドラー メソッドを定義します。  たとえばイベントがデリゲート型 <xref:System.EventHandler> に基づいている場合は、次のコードがメソッド スタブになります。  
  
    ```  
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  加算代入演算子 \(`+=`\) を使用して、イベントにイベント ハンドラーをアタッチします。  次の例では、オブジェクト `publisher` に `RaiseCustomEvent` という名前のイベントがあることを想定しています。  サブスクライバー クラスがイベントをサブスクライブするには、パブリッシャー クラスの参照が必要です。  
  
    ```  
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     これは、C\# 2.0 で新しく導入された構文です。  `new` キーワードを使用してカプセル化する側のデリゲートを明示的に作成する必要がある点では、C\# 1.0 の構文と同じです。  
  
    ```  
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     イベント ハンドラーは、ラムダ式を使用して追加することもできます。  
  
    ```  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     詳細については、「[方法: LINQ 以外でラムダ式を使用する](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md)」を参照してください。  
  
### 匿名メソッドを使用してイベントをサブスクライブするには  
  
-   後でイベントのサブスクリプションを解除する必要がない場合は、加算代入演算子 \(`+=`\) を使用して、イベントに匿名メソッドをアタッチします。  次の例では、オブジェクト `publisher` に `RaiseCustomEvent`  という名前のイベントがあり、特別なイベント情報を格納する `CustomEventArgs` クラスが定義されていることを想定しています。  サブスクライバー クラスがイベントをサブスクライブするには、`publisher` の参照が必要です。  
  
    ```  
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     匿名関数を使用してイベントをサブスクライブした場合は、簡単にサブスクリプションを解除できない点に注意してください。  この場合、サブスクリプションを解除するには、イベントをサブスクライブしたコードに戻り、匿名メソッドをデリゲート変数に格納して、このデリゲートをイベントに追加する必要があります。  通常は、後でコード内のイベントからサブスクリプションを解除する必要がある場合、イベントのサブスクライブに匿名関数を使用しないことをお勧めします。  匿名関数の詳細については、「[匿名関数](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)」を参照してください。  
  
## サブスクリプション解除  
 イベントの発生時にイベント ハンドラーが呼び出されるのを防ぐには、イベント サブスクリプションを解除します。  リソースのリークを防ぐには、サブスクライバー オブジェクトを破棄する前にイベント サブスクリプションを解除する必要があります。  イベント サブスクリプションを解除しない限り、パブリッシャー オブジェクト内のイベントの基礎となるマルチキャスト デリゲートは、サブスクライバーのイベント ハンドラーをカプセル化するデリゲートを参照します。  パブリッシャー オブジェクトに参照が含まれている限り、ガベージ コレクションはサブスクライバー オブジェクトを削除しません。  
  
#### イベント サブスクリプションを解除するには  
  
-   減算代入演算子 \(`-=`\) を使用して、イベント サブスクリプションを解除します。  
  
    ```  
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     すべてのサブスクライバーのサブスクリプションが解除されたら、パブリッシャー クラス内のイベント インスタンスが `null` に設定されます。  
  
## 参照  
 [イベント](../../../csharp/programming-guide/events/index.md)   
 [event](../../../csharp/language-reference/keywords/event.md)   
 [方法 : .NET Framework ガイドラインに準拠したイベントを発行する](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)   
 [\-\= 演算子](../../../csharp/language-reference/operators/subtraction-assignment-operator-1.md)   
 [\+\= 演算子](../../../csharp/language-reference/operators/addition-assignment-operator.md)