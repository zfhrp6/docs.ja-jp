---
title: "方法 : ルーティング イベントのクラス処理を追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "クラス ハンドラー, ルーティング イベント"
  - "ルーティング イベント, クラス ハンドラー"
  - "task_core_add_class_handling_routed_event"
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : ルーティング イベントのクラス処理を追加する
ルーティング イベントは、クラス ハンドラーまたはルート内の特定のノードにあるインスタンスで処理できます。  クラス ハンドラーが最初に呼び出され、このクラス ハンドラーをクラス実装が使用してインスタンス処理からのイベントの出力を抑制したり、基本クラスが所有するイベントに他のイベント固有の動作を導入できます。  次の例では、クラス ハンドラーを実装するための、非常に密接に関連する 2 つの手法を示します。  
  
## 使用例  
 この例では、<xref:System.Windows.Controls.Canvas> パネルに基づくカスタム クラスを使用します。  子要素クラスまたはその上にあるインスタンス ハンドラーが呼び出される前に、左のマウス ボタンのすべてのクリックをインターセプトし、それらを処理済みとしてマークするなど、カスタム クラスがその子要素に動作を導入していることが、アプリケーションの基本前提になります。  
  
 <xref:System.Windows.UIElement> クラスは、<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> イベントを単純にオーバーライドして、そのイベントでクラス処理を有効にする仮想メソッドを公開します。  これは、仮想メソッドがクラスの階層内のどこかで使用できる場合の、最も単純なクラス処理の実装方法です。  次のコードは、<xref:System.Windows.Controls.Canvas> から派生した "MyEditContainer" での <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> の実装を示します。  この実装では、引数でイベントを処理済みとしてマークしてから、ソース要素に基本的な表示変更を与えるコードを追加します。  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 基本クラスまたはその特定のメソッドに対して仮想メソッドが使用できない場合、クラス処理は <xref:System.Windows.EventManager> クラスのユーティリティ メソッド <xref:System.Windows.EventManager.RegisterClassHandler%2A> を使用して直接追加できます。  このメソッドは、クラス処理を追加しているクラスの静的な初期化内でのみ呼び出す必要があります。  この例では、<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> の別のハンドラーを追加します。この場合、登録済みのクラスがカスタム クラスになります。  これに対し、仮想メソッドを使用している場合は、登録済みのクラスは実際に <xref:System.Windows.UIElement> の基本クラスになります。  基本クラスとサブクラスがそれぞれクラス処理を登録している場合、サブクラスのハンドラーが最初に呼び出されます。  この場合のアプリケーションの動作は、まずこのハンドラーにそのメッセージ ボックスが表示されてから、仮想メソッドのハンドラーのビジュアルな変更が示されます。  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## 参照  
 <xref:System.Windows.EventManager>   
 [ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)   
 [ルーティング イベントを処理する](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)   
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)