---
title: "Overview of the Visual Basic Application Model | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Application object, Visual Basic application model"
  - "Visual Basic application model"
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# Overview of the Visual Basic Application Model
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、Windows フォーム アプリケーションの動作を制御するための確たるモデルが用意されています。それが [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] アプリケーション モデルです。  このモデルには、アプリケーションの起動とシャットダウンを処理するためのイベントや、未処理の例外をキャッチするためのイベントがあります。  また、単一インスタンス アプリケーションの開発もサポートされています。  このアプリケーション モデルには拡張性があるため、開発者は、きめ細かな制御が必要な場合には、オーバーライド可能なメソッドをカスタマイズできます。  
  
## アプリケーション モデルの用途  
 一般に、アプリケーションでは、起動時と終了時にタスクを実行する必要があります。  たとえば、アプリケーションの起動時には、スプラッシュ スクリーンの表示、データベース接続の確立、保存しておいた状態の読み込みなどを実行できます。  アプリケーションの終了時には、データベース接続のクローズや現在の状態の保存などを実行できます。  また、アプリケーションは、未処理の例外の発生時など、予測できない形で終了するときに、独自のコードを実行できます。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] アプリケーション モデルでは、*単一インスタンス* アプリケーションを簡単に作成できます。  単一インスタンス アプリケーションが通常のアプリケーションと違うのは、当該アプリケーションのインスタンスは一度に 1 つのみ実行できるということです。  単一インスタンス アプリケーションの別のインスタンスを二重起動しようとすると、元のインスタンスに対して、その旨が `StartupNextInstance` イベントにより通知されます。  この通知には、二重起動されたインスタンスのコマンド ライン引数が含まれています。  そして、二重起動されたインスタンスは、初期化が実行される前の段階で閉じられます。  
  
 単一インスタンス アプリケーションの起動時には、それが当該アプリケーションの最初のインスタンスなのか、それとも二重起動されたインスタンスなのかがチェックされます。  
  
-   最初のインスタンスの場合には、通常どおり起動されます。  
  
-   最初のインスタンスの実行中に、同じアプリケーションを二重起動しようとした場合には、実行される動作は異なります。  二重起動の場合は、最初のインスタンスに対してコマンド ライン引数が通知され、すぐに終了されます。  最初のインスタンスは、`StartupNextInstance` イベントを処理し、二重起動されたインスタンスのコマンド ライン引数を判断したうえで、実行を継続します。  
  
     この図は、二重起動されたインスタンスから最初のインスタンスに対する通知方法を示しています。  
  
     ![単一インスタンス アプリケーション イメージ](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.gif "SingleInstance")  
  
 `StartupNextInstance` イベントを処理すると、単一インスタンス アプリケーションの動作を制御できます。  たとえば、Microsoft Outlook は、通常は単一インスタンス アプリケーションとして動作します。Outlook が実行中のときに、Outlook を再度起動しようとすると、元のインスタンスにフォーカスが移り、新しいインスタンスは開かれません。  
  
## アプリケーション モデルのイベント  
 以下に示すのは、アプリケーション モデルに含まれているイベントです。  
  
-   **アプリケーションの起動**。  アプリケーションの起動時には <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> イベントが発生します。  このイベントを処理すると、メイン フォームの読み込み前にアプリケーションを初期化するコードを追加できます。  `Startup` イベントには、起動処理のその段階でアプリケーションの実行を必要に応じてキャンセルするための方法も用意されています。  
  
     アプリケーションの構成により、スタートアップ コードの実行時にスプラッシュ スクリーンを表示させることができます。  アプリケーション モデルの既定では、`/nosplash` または `-nosplash` のいずれかのコマンド ライン引数が指定されている場合、スプラッシュ スクリーンは表示されません。  
  
-   **単一インスタンス アプリケーション**。  単一インスタンス アプリケーションが二重起動されたときには、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> イベントが発生します。  このイベントは、二重起動されたインスタンスのコマンド ライン引数を渡します。  
  
-   **未処理の例外**。  アプリケーションは未処理の例外を検出すると <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> イベントを発生させます。  このイベントのハンドラーでは、例外を調べ、実行を続けるかどうかを決定できます。  
  
     `UnhandledException` イベントは、状況によっては発生しない場合もあります。  詳細については、「<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>」を参照してください。  
  
-   **ネットワーク接続の変更**。  コンピューターのネットワークの可用性が変更された場合、アプリケーションでは <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged> イベントが発生します。  
  
     `NetworkAvailabilityChanged` イベントは、状況によっては発生しない場合もあります。  詳細については、「<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>」を参照してください。  
  
-   **アプリケーションの終了**。  アプリケーションには、終了しようとしている旨を通知するための <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> イベントが用意されています。  このイベント ハンドラーでは、アプリケーションで実行する必要のある操作 \(たとえばクローズや保存など\) が完了したかどうかを確認できます。  アプリケーションの構成により、メイン フォームが閉じたときに終了するか、それとも、すべてのフォームが閉じたときにのみ終了するかを設定できます。  
  
## 可用性  
 既定では、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] アプリケーション モデルは Windows フォーム プロジェクトで利用できます。  異なるスタートアップ オブジェクトを利用するようにアプリケーションを構成した場合や、カスタムの `Sub Main` でアプリケーション コードを開始する場合は、そのオブジェクトまたはクラスで <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> クラスの実装を用意しないと、アプリケーション モデルを利用できない場合があります。  スタートアップ オブジェクトの変更については、「[\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Extending the Visual Basic Application Model](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)