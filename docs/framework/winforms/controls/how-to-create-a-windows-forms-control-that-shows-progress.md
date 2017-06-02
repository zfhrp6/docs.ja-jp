---
title: "方法 : 進行状況を示す Windows フォーム コントロールを作成する | Microsoft Docs"
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
  - "コントロール [Windows フォーム], 作成"
  - "コントロール [Windows フォーム], 進行状況の追跡"
  - "FlashTrackBar カスタム コントロール"
  - "進行状況, 報告 [Windows フォーム]"
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : 進行状況を示す Windows フォーム コントロールを作成する
アプリケーションのレベルまたは進行状況を表示するために使用できる `FlashTrackBar` というカスタム コントロールのコード例を次に示します。  このコントロールは、グラデーションを使用して進行状況を表示します。  
  
 `FlashTrackBar` コントロールには次のような機能が含まれます。  
  
-   カスタム プロパティの定義。  
  
-   カスタム イベントの定義  \(`FlashTrackBar` は `ValueChanged` イベントを定義します\)。  
  
-   コントロールを描画するロジックを提供するための、<xref:System.Windows.Forms.Control.OnPaint%2A> メソッドのオーバーライド。  
  
-   <xref:System.Windows.Forms.Control.ClientRectangle%2A> プロパティを使用した、コントロールの描画に利用できる領域の計算。  `FlashTrackBar` は、`OptimizedInvalidate` メソッドでこの計算を実行します。  
  
-   Windows フォーム デザイナー内でプロパティが変更されたときの、プロパティのシリアル化または永続化の実装。  `FlashTrackBar` は `StartColor` プロパティと `EndColor` プロパティをシリアル化するために、`ShouldSerializeStartColor` メソッドと `ShouldSerializeEndColor` メソッドを定義します。  
  
 `FlashTrackBar` によって定義されるカスタム プロパティを次の表に示します。  
  
|プロパティ|Description|  
|-----------|-----------------|  
|`AllowUserEdit`|ユーザーがフラッシュ トラック バーをクリックまたはドラッグして値を変更できるかどうかを示します。|  
|`EndColor`|トラック バーの終了色を指定します。|  
|`DarkenBy`|前景のグラデーションを基準にして、背景のグラデーションをどの程度の濃さにするかを指定します。|  
|`Max`|トラック バーの最大値を指定します。|  
|`Min`|トラック バーの最小値を指定します。|  
|`StartColor`|グラデーションの開始色を指定します。|  
|`ShowPercentage`|グラデーションの上にパーセントを表示するかどうかを示します。|  
|`ShowValue`|グラデーションの上に現在の値を表示するかどうかを示します。|  
|`ShowGradient`|現在の値を表示した色のグラデーションをトラック バーに表示するかどうかを示します。|  
|-   `Value`|トラック バーの現在の値を指定します。|  
  
 次の表は、`FlashTrackBar` によって定義される追加メンバーである、プロパティ変更イベント、およびイベントを発生させるメソッドを示しています。  
  
|メンバー|Description|  
|----------|-----------------|  
|`ValueChanged`|トラック バーの `Value` プロパティが変更されたときに発生するイベント。|  
|`OnValueChanged`|`ValueChanged` イベントを発生させるメソッド。|  
  
> [!NOTE]
>  `FlashTrackBar` では、イベント データに <xref:System.EventArgs> クラスを使用し、イベント デリゲートに <xref:System.EventHandler> を使用します。  
  
 対応する *EventName* イベントを処理するために、`FlashTrackBar` は <xref:System.Windows.Forms.Control?displayProperty=fullName> から継承した次のメソッドをオーバーライドします。  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 対応するプロパティ変更イベントを処理するために、`FlashTrackBar` は <xref:System.Windows.Forms.Control?displayProperty=fullName> から継承した次のメソッドをオーバーライドします。  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## 使用例  
 `FlashTrackBar` コントロールは、次のコード一覧に示すとおり、`FlashTrackBarValueEditor` と `FlashTrackBarDarkenByEditor` という 2 つの UI 型エディターを定義します。  `HostApp` クラスは、Windows フォームで `FlashTrackBar` コントロールを使用します。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## 参照  
 [Extending Design\-Time Support](../Topic/Extending%20Design-Time%20Support.md)   
 [Windows フォーム コントロール開発の基本概念](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)