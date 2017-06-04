---
title: "方法 : Web フォーム アプリケーションでイベントを利用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "イベント [.NET Framework]、Web フォーム"
  - "Web フォーム コントロール、およびイベント"
  - "イベントハンドラー [.NET Framework]、Web フォーム"
  - "イベント [.NET Framework]、使用"
  - "Web フォーム、イベント処理"
ms.assetid: 73bf8638-c4ec-4069-b0bb-a1dc79b92e32
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# 方法 : Web フォーム アプリケーションでイベントを利用する
ASP.NET Web フォーム アプリケーションの一般的なシナリオに応じて特定のアクション コントロールをユーザーがクリックするかをにコントロールと Web ページを設定する場合は、次に実行します。  たとえば、<xref:System.Web.UI.WebControls.Button?displayProperty=fullName> のコントロールは、ユーザーが Web ページでクリックしたときに、イベントを発生させます。  そのイベントを処理することで、アプリケーションでは、そのボタンのクリックに対して適切なアプリケーション ロジックを実行できます。  
  
### Web ページ上のボタン クリック イベントを処理するには  
  
1.  、次のステップで定義するメソッドの名前に `OnClick` の値が設定されている <xref:System.Web.UI.WebControls.Button> のコントロールを含む ASP.NET Web ページ \(Web フォーム ページ\) を作成します。  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  `OnClick` 値の名前があり、<xref:System.Web.UI.WebControls.Button.Click> イベントのデリゲート シグネチャに一致する定義するイベント ハンドラーを定義します。  
  
    ```csharp  
    protected void Button1_Click(object sender, EventArgs e)  
    {  
        // perform action  
    }  
    ```  
  
    ```vb  
    Protected Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' perform action  
    End Sub  
    ```  
  
     <xref:System.Web.UI.WebControls.Button.Click> イベントでは、デリゲート型に <xref:System.EventHandler> クラスを使用し、イベント データに <xref:System.EventArgs> クラスを使用します。  ASP.NET ページ フレームワークは、自動的に <xref:System.EventHandler> のインスタンスを作成し、<xref:System.Web.UI.WebControls.Button> インスタンスの <xref:System.Web.UI.WebControls.Button.Click> イベント、このデリゲート インスタンスを追加するコードを生成します。  
  
3.  手順 2 で定義したイベント ハンドラー メソッドでは、イベントが発生したときに必要な操作を実行するコードを追加します。  
  
## 参照  
 [イベント](../../../docs/standard/events/index.md)