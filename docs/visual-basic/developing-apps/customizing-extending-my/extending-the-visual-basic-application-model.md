---
title: "Extending the Visual Basic Application Model | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic Application Model, extending"
ms.assetid: e91d3bed-4c27-40e3-871d-2be17467c72c
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Extending the Visual Basic Application Model
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> クラスの `Overridable` メンバーをオーバーライドすることによって、アプリケーション モデルに対して機能を追加できます。  このテクニックを使用すると、アプリケーション モデルの動作をカスタマイズしたり、アプリケーションの起動時および終了時に独自のメソッドの呼び出しを追加したりできます。  
  
## アプリケーション モデルの視覚的な概要  
 このセクションでは、Visual Basic アプリケーション モデルにおける関数呼び出しのシーケンスを視覚的に示します。  各関数の目的については、この後のセクションで詳しく説明します。  
  
 次の図は、一般的な Visual Basic Windows フォーム アプリケーションにおけるアプリケーション モデルの呼び出しシーケンスを示しています。  シーケンスは `Sub Main` プロシージャによる <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> メソッドの呼び出しで始まります。  
  
 ![Visual Basic アプリケーション モデル &#45;&#45; 実行](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelrun.gif "VB\_ModelRun")  
  
 Visual Basic アプリケーション モデルでは、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> イベントと <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> イベントも使用できます。  次の図は、これらのイベントが発生するしくみを示しています。  
  
 ![Visual Basic アプリケーション モデル &#45;&#45; 次のインスタンス](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_modelnext.gif "VB\_ModelNext")  
  
 ![Visual Basic アプリケーション モデル ハンドルされていない例外](../../../visual-basic/developing-apps/customizing-extending-my/media/vb_unhandex.gif "VB\_UnhandEx")  
  
## 基本メソッドのオーバーライド  
 `Application` のメソッドが実行される順序は、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> メソッドにより定義されます。  既定では、Windows フォーム アプリケーションの `Sub Main` プロシージャから <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> メソッドが呼び出されます。  
  
 アプリケーションが通常のアプリケーション \(複数インスタンス アプリケーション\) の場合、または単一インスタンス アプリケーションの最初のインスタンスの場合には、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Run%2A> メソッドは一連の `Overridable` メソッドを次の順序で実行します。  
  
1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A>.  既定では、このメソッドは、メイン アプリケーション スレッドについて、visual スタイル、テキスト表示スタイル、および \(アプリケーションに Windows 認証が使用されている場合\) 現在のプリンシパルを設定し、コマンド ライン引数に `/nosplash` も `-nosplash` も指定されなかった場合は、`ShowSplashScreen` を呼び出します。  
  
     この関数が `False` を返した場合、アプリケーションの起動処理はキャンセルされます。  これは、状況に応じてアプリケーションの実行が不要な場合に役立ちます。  
  
     <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> メソッドは以下のメソッドを呼び出します。  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A>.  アプリケーションにスプラッシュ スクリーンが定義されているかどうかを判断し、定義されている場合はそのスプラッシュ スクリーンを別スレッドで表示します。  
  
         <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShowSplashScreen%2A> メソッドには、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A> プロパティで指定されたミリ秒以上スプラッシュ スクリーンを表示するコードが含まれています。  この機能を使用するためには、**プロジェクト デザイナー**を使用してアプリケーションにスプラッシュ スクリーンを追加するか \(この場合は `My.Application.MinimumSplashScreenDisplayTime` プロパティは 2 秒に設定されます\)、または <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnInitialize%2A> メソッドか <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> メソッドをオーバーライドするメソッドで `My.Application.MinimumSplashScreenDisplayTime` プロパティを設定する必要があります。  詳細については、「<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MinimumSplashScreenDisplayTime%2A>」を参照してください。  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A>.  スプラッシュ スクリーンを初期化するコードをデザイナーが追加できます。  
  
         既定では、このメソッドは何も実行しません。  ただし、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の**プロジェクト デザイナー**でアプリケーションのスプラッシュ スクリーンを選択した場合、デザイナーが <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateSplashScreen%2A> メソッドをオーバーライドし、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A> プロパティがスプラッシュ スクリーン フォームの新しいインスタンスに設定されます。  
  
2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartup%2A>.  `Startup` イベントの発生を機能拡張するための部分です。  この関数が `False` を返した場合、アプリケーションの起動処理は中断されます。  
  
     既定では、このメソッドは <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> イベントを発生させます。  イベント ハンドラーが、イベント引数の <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> プロパティを `True` に設定した場合、このメソッドは `False` を返し、アプリケーションの起動処理はキャンセルされます。  
  
3.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnRun%2A>.  初期化の完了後、メイン アプリケーションが実行される開始点を提供します。  
  
     既定では、このメソッドは、Windows フォームのメッセージ ループに入る前に、`OnCreateMainForm` メソッド \(アプリケーションのメイン フォームを作成するため\) および `HideSplashScreen` メソッド \(スプラッシュ スクリーンを閉じるため\) を呼び出します。  
  
    1.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>.  メイン フォームを初期化するコードをデザイナーが追加するための手段を提供します。  
  
         既定では、このメソッドは何も実行しません。  ただし、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の**プロジェクト デザイナー**でアプリケーションのメイン フォームを選択した場合、デザイナーが <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> メソッドをオーバーライドし、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> プロパティがメイン フォームの新しいインスタンスに設定されます。  
  
    2.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.HideSplashScreen%2A>.  スプラッシュ スクリーンが定義されているアプリケーションで、スプラッシュ スクリーンが開かれている場合には、このメソッドがそれを閉じます。  
  
         既定では、このメソッドはスプラッシュ スクリーンを閉じます。  
  
4.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A>.  単一インスタンス アプリケーションのインスタンスが二重起動されたときの動作をカスタマイズする手段を提供します。  
  
     既定では、このメソッドは <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance> イベントを発生させます。  
  
5.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnShutdown%2A>.  `Shutdown` イベントの発生を機能拡張するための部分です。  このメソッドは、メイン アプリケーションで未処理の例外が発生した場合には実行されません。  
  
     既定では、このメソッドは <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> イベントを発生させます。  
  
6.  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnUnhandledException%2A>.  上記のいずれかのメソッドで未処理の例外が発生したときに実行されます。  
  
     既定では、デバッガーがアタッチされておらず、かつアプリケーションが `UnhandledException` イベントを処理している場合に、このメソッドは <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> イベントを発生させます。  
  
 単一インスタンス アプリケーションの場合で、同じアプリケーションが既に実行中のときには、二重起動された方のインスタンスは、同じアプリケーションの元のインスタンスの <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnStartupNextInstance%2A> メソッドを呼び出し、自らは終了します。  
  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> コンストラクターは <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> プロパティを呼び出して、アプリケーションのフォームにどのテキスト描画エンジンを使用するかを判断します。  既定では、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> プロパティは `False` を返します。これは [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] の既定である GDI テキスト描画エンジンが使用されることを示します。  <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UseCompatibleTextRendering%2A> プロパティは、`True` を返すようにオーバーライドできます。この値は、Visual Basic .NET 2002 および Visual Basic .NET 2003 の既定である GDI\+ のテキスト描画エンジンが使用されることを示します。  
  
## アプリケーションの構成  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] アプリケーション モデルの一環として、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> クラスには、アプリケーションを構成するプロテクト プロパティが用意されています。  これらのプロパティは、実装するクラスのコンストラクターで設定する必要があります。  
  
 既定の Windows フォーム プロジェクトでは、**プロジェクト デザイナー**は、デザイナーの設定でこれらのプロパティを設定するコードを作成します。  これらのプロパティが使用されるのはアプリケーションの起動時のみです。アプリケーションが起動された後で値を設定しても効果はありません。  
  
||||  
|-|-|-|  
|プロパティ|意味|プロジェクト デザイナーのアプリケーション ウィンドウの配置|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.IsSingleInstance%2A>|アプリケーションが単一インスタンス アプリケーションまたは複数インスタンス アプリケーションとして動作するかどうかを表します。|の チェック ボックス**\[単一インスタンス アプリケーションを作成します。\]**|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.EnableVisualStyles%2A>|アプリケーションがWindows XPに一致する視覚スタイルを使用します。|の チェック ボックス**\[XPの視覚スタイルを有効にします。\]**|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SaveMySettingsOnExit%2A>|アプリケーションの終了時に、ユーザー設定の変更をアプリケーションが自動的に保存するかどうかを表します。|の チェック ボックス**\[シャットダウン時My.Settingsを保存します。\]**|  
|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.ShutdownStyle%2A>|アプリケーションが終了すると、などのスタートアップ フォームが閉じたとき、または最後のフォームが閉じたとき。|**\[シャットダウン モード\]** の一覧|  
  
## 参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Overview of the Visual Basic Application Model](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)   
 [\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](../Topic/Application%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)