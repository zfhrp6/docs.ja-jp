---
title: "方法 : どの修飾子キーが押されたかを判断する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Alt キー"
  - "Ctrl キー"
  - "イベント [Windows フォーム], キーボード"
  - "イベント [Windows フォーム], マウス"
  - "キーボード入力"
  - "キーボード, キーボード入力"
  - "キー, Alt キー"
  - "キー, Ctrl キー"
  - "キー, 判断 (最後に押された)"
  - "キー, 修飾子キー"
  - "キー, Shift キー"
  - "Keys.Alt 列挙型メンバー"
  - "Keys.ControlKey 列挙型メンバー"
  - "Keys.Shift 列挙型メンバー"
  - "修飾子キー"
  - "Shift キー"
  - "ユーザー入力, チェック (キーボードを)"
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : どの修飾子キーが押されたかを判断する
ユーザーのキーストロークを受け付けるアプリケーションを作成するときに、Shift、Alt、Ctrl などの修飾子キーの監視が必要になる場合があります。  他のキーまたはマウスのクリックと組み合わせて修飾子キーが押された場合、アプリケーションはそれに応じて適切な処理を実行できます。  たとえば、S キーを押した場合は単に画面上に "s" が表示されますが、Ctrl キーを押しながら S キーを押した場合は現在のドキュメントが保存されます。  <xref:System.Windows.Forms.Control.KeyDown> イベントを処理する場合、イベント ハンドラーが受け取る <xref:System.Windows.Forms.KeyEventArgs> の <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> プロパティは、どの修飾子キーが押されたかを指定します。  また、<xref:System.Windows.Forms.KeyEventArgs> の <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> プロパティは、押された文字およびビットごとの OR と結合された修飾子キーを指定します。  ただし、<xref:System.Windows.Forms.Control.KeyPress> イベントやマウス イベントを処理する場合、イベント ハンドラーはこの情報を受け取りません。  その場合は、<xref:System.Windows.Forms.Control> クラスの <xref:System.Windows.Forms.Control.ModifierKeys%2A> プロパティを使用する必要があります。  いずれの場合も、適切な <xref:System.Windows.Forms.Keys> 値とテスト対象の値について、ビットごとの AND を実行する必要があります。  <xref:System.Windows.Forms.Keys> 列挙型には修飾子キーごとのバリエーションが用意されているため、正しい値を使用してビットごとの AND を実行することが重要です。  たとえば、Shift キーは、<xref:System.Windows.Forms.Keys>、<xref:System.Windows.Forms.Keys>、<xref:System.Windows.Forms.Keys>、および <xref:System.Windows.Forms.Keys> で表されます。修飾子キーとしての Shift キーをテストするための正しい値は <xref:System.Windows.Forms.Keys> です。  同様に、修飾子キーとしての Ctrl キーおよび Alt キーをテストするには、それぞれ <xref:System.Windows.Forms.Keys> 値および <xref:System.Windows.Forms.Keys> 値を使用する必要があります。  
  
> [!NOTE]
>  Visual Basic プログラマは <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> プロパティを介してキー情報にアクセスすることもできます。  
  
### どの修飾キーが押されたかを判断するには  
  
-   特定の修飾子キーが押されたかどうかを判断するには、ビットごとの `AND` 演算子を <xref:System.Windows.Forms.Control.ModifierKeys%2A> プロパティおよび <xref:System.Windows.Forms.Keys> 列挙型の値と組み合わせて使用します。  <xref:System.Windows.Forms.Control.KeyPress> イベント ハンドラー内で Shift キーが押されたかどうかを判断する方法を次のコード例に示します。  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## 参照  
 <xref:System.Windows.Forms.Keys>   
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>   
 [Windows フォーム アプリケーションにおけるキーボード入力](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)   
 [How to: Determine If CapsLock is On in Visual Basic](http://msdn.microsoft.com/ja-jp/91e60f5c-dd61-4222-ba5f-39af803afd8c)