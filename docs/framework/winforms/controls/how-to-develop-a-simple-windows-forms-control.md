---
title: "方法 : シンプルな Windows フォーム コントロールを開発する | Microsoft Docs"
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
  - "Control クラス, Windows フォーム"
  - "コントロール [Windows フォーム]"
  - "カスタム コントロール [Windows フォーム], 作成 (コードを使用して簡単なコントロールを)"
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : シンプルな Windows フォーム コントロールを開発する
ここでは、カスタム Windows フォーム コントロールの作成手順を示します。  この手順では、<xref:System.Windows.Forms.Control.Text%2A> プロパティの配列を変更できるシンプルなコントロールを作成します。  このコントロールでは、イベントの発生や処理は行われません。  
  
### シンプルなカスタム コントロールを作成するには  
  
1.  <xref:System.Windows.Forms.Control?displayProperty=fullName> から派生するクラスを定義します。  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control{}  
    ```  
  
2.  プロパティを定義します。  コントロールは <xref:System.Windows.Forms.Control> クラスから多数のプロパティを継承するため、プロパティの定義は必須ではありません。ただし、ほとんどのカスタム コントロールでは追加プロパティを定義します。`TextAlignment`  というプロパティを定義するコード片を次に示します。このプロパティは、`FirstControl`  が、<xref:System.Windows.Forms.Control> から継承した <xref:System.Windows.Forms.Control.Text%2A> プロパティの表示形式を設定するときに使用するプロパティです。  プロパティの定義の詳細については、「[プロパティの概要](../Topic/Properties%20Overview.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     コントロールのビジュアル表示を変更するプロパティを設定するには、<xref:System.Windows.Forms.Control.Invalidate%2A> メソッドを呼び出して、コントロールを再描画する必要があります。  <xref:System.Windows.Forms.Control.Invalidate%2A> は基本クラス <xref:System.Windows.Forms.Control> で定義されます。  
  
3.  <xref:System.Windows.Forms.Control> から継承された <xref:System.Windows.Forms.Control.OnPaint%2A> プロテクト メソッドをオーバーライドして、レンダリング ロジックをコントロールに追加します。  <xref:System.Windows.Forms.Control.OnPaint%2A> をオーバーライドしないと、作成するコントロールがそのコントロール自体を描画できません。  <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドが <xref:System.Windows.Forms.Control> から継承した <xref:System.Windows.Forms.Control.Text%2A> プロパティを、`alignmentValue` フィールドによって指定された配置で表示するコード片を次に示します。  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  コントロールの属性を指定します。  デザイン時には、ビジュアル デザイナーではこれらの属性を使用して、コントロール、コントロールのプロパティとイベントが適切に表示されます。  `TextAlignment` プロパティに属性を適用するコード片を次に示します。  Visual Studio などのデザイナーでは、次のコード片に示されている <xref:System.ComponentModel.CategoryAttribute.Category%2A> 属性によって、プロパティが論理カテゴリの下に表示されます。  <xref:System.ComponentModel.DescriptionAttribute.Description%2A> 属性が適用されている場合には、`TextAlignment` プロパティが選択されると、**\[プロパティ\]** ウィンドウ下部に説明文字列が表示されます。  属性の詳細については、「[コンポーネントのデザイン時属性](../Topic/Design-Time%20Attributes%20for%20Components.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  \(省略可能\) コントロールに対してリソースを指定します。  コントロールに対してビットマップなどのリソースを指定するには、コンパイラ オプション \(C\# の `/res` など\) を使用して、コントロールにリソースをパッケージ化します。  実行時には、<xref:System.Resources.ResourceManager> クラスのメソッドを使用してリソースを取得できます。  リソースの作成と使用の詳細については、「[デスクトップ アプリケーションのリソース](../../../../docs/framework/resources/index.md)」を参照してください。  
  
6.  コンパイルしてコントロールを配置します。  `FirstControl` をコンパイルして配置するには、次の手順に従います。  
  
    1.  次のサンプルのコードをソース ファイル \(FirstControl.cs または FirstControl.vb など\) に保存します。  
  
    2.  ソース コードをコンパイルして、アセンブリを生成します。アプリケーションのディレクトリにこのアセンブリを保存します。  この処理を行うには、ソース ファイルが格納されているディレクトリで次のコマンドを実行します。  
  
        ```vb  
        vbc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```csharp  
        csc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.cs  
        ```  
  
         `/t:library` コンパイラ オプションによって、作成するアセンブリが実行可能ファイルではなくライブラリであることがコンパイラに指示されます。  `/out` オプションには、アセンブリの名前とパスを指定します。  `/r` オプションには、コードがアセンブリを参照するときのアセンブリ名を指定します。  上記のコード例で作成されるアセンブリは、開発者が作成したアプリケーションだけで使用できるプライベート アセンブリです。  したがって、このアセンブリを各自のアプリケーションのディレクトリに保存する必要があります。  配布用にコントロールをパッケージ化および配置する方法の詳細については、「[配置](../../../../docs/framework/deployment/net-framework-and-applications.md)」を参照してください。  
  
 `FirstControl` のコードのサンプルを次に示します。  このコントロールは、`CustomWinControls` 名前空間に格納されています。  名前空間では、関連する型を論理的にグループ化できます。  コントロールを作成するには、既存の名前空間を使用するか、または名前空間を新規作成して使用します。  C\# では、`using` 宣言 \(Visual Basic の場合は `Imports`\) を使用すると、名前空間から型へアクセスするときに、型の完全限定名を使用する必要がありません。  次の例では、`using` 宣言によって、コードは完全修飾名 <xref:System.Windows.Forms.Control?displayProperty=fullName> を使用せずに単純に <xref:System.Windows.Forms.Control> として <xref:System.Windows.Forms?displayProperty=fullName> から <xref:System.Windows.Forms.Control> クラスにアクセスできます。  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## フォームでのカスタム コントロールの使用  
 `FirstControl` を使用するシンプルなフォームの例を次に示します。  この例では、`FirstControl` のインスタンスを 3 つ作成します。それぞれのインスタンスでは、`TextAlignment` プロパティに異なる値が設定されます。  
  
#### このサンプルをコンパイルして実行するには  
  
1.  次に示すサンプルのコードをソース ファイル \(SimpleForm.cs または SimpleForms.vb\) に保存します。  
  
2.  ソース ファイルが格納されているディレクトリで次のコマンドを実行することにより、実行可能アセンブリへソース コードをコンパイルします。  
  
    ```vb  
    vbc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```csharp  
    csc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     CustomWinControls.dll は、`FirstControl` クラスが含まれているアセンブリです。  フォームがこのアセンブリへアクセスできるように、このアセンブリはソース ファイル \(SimpleForm.cs または SimpleForms.vb\) と同じディレクトリに格納されている必要があります。  
  
3.  次に示すコマンドで SimpleForm.exe を実行します。  
  
    ```  
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## 参照  
 [Windows フォーム コントロールのプロパティ](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)   
 [Windows フォーム コントロールのイベント](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)