---
title: "方法 : Web フォーム アプリケーションでイベントを利用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [.NET Framework], Web Forms
- Web Forms controls, and events
- event handlers [.NET Framework], Web Forms
- events [.NET Framework], consuming
- Web Forms, event handling
ms.assetid: 73bf8638-c4ec-4069-b0bb-a1dc79b92e32
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bdb0a6be309f27348ba13bf93fd5aedd3c66a792
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a>方法 : Web フォーム アプリケーションでイベントを利用する
コントロールと web ページを作成し、ユーザーがクリックしたコントロールに基づく特定のアクションを実行する ASP.NET Web フォーム アプリケーションで一般的なシナリオです。 たとえば、<xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType>コントロールをユーザーが web ページでクリックしたときにイベントを発生させます。 イベントを処理することによって、アプリケーションは、そのボタンをクリックし、適切なアプリケーション ロジックを実行できます。  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Web ページ上のボタン クリック イベントを処理するには  
  
1.  ASP.NET Web フォーム ページ (web ページ) を作成、<xref:System.Web.UI.WebControls.Button>と制御、`OnClick`値は、次の手順で定義するメソッドの名前に設定します。  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  一致するイベント ハンドラーを定義する、<xref:System.Web.UI.WebControls.Button.Click>イベントのデリゲート シグネチャし名前を持つ、に対して定義されている、`OnClick`値。  
  
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
  
     <xref:System.Web.UI.WebControls.Button.Click>イベントを使用して、<xref:System.EventHandler>はデリゲート型のクラスと<xref:System.EventArgs>イベント データ クラスです。 ASP.NET ページ フレームワークのインスタンスを作成するコードを自動的に生成する<xref:System.EventHandler>をこのデリゲート インスタンスを追加し、<xref:System.Web.UI.WebControls.Button.Click>のイベント、<xref:System.Web.UI.WebControls.Button>インスタンス。  
  
3.  イベント ハンドラー メソッドを手順 2. で定義されているは、イベントが発生したときに必要なすべてのアクションを実行するコードを追加します。  
  
## <a name="see-also"></a>関連項目  
 [イベント](../../../docs/standard/events/index.md)
