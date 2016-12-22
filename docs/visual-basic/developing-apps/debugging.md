---
title: "Debugging Your Visual Basic Application | Microsoft Docs"
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
  - "debugging [Visual Basic], common tasks"
ms.assetid: 904760b8-9fe9-42a7-9d65-d93774253219
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Debugging Your Visual Basic Application
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

このページでは、[!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)] に組み込まれているデバッグ機能に関するドキュメントへのリンクを示します。  たとえば、デバッガー自体の実行時の動作を監視することで、アプリケーションのセマンティック エラーを検出できます。  
  
 デバッガーを使用すると、変数値を出力するための追加の呼び出しを挿入せずに、アプリケーションの変数値をチェックできます。  同様に、指定した位置で実行を中断するためのブレークポイントをコードに挿入することもできます。  
  
## 実行の制御  
 次の表は、実行制御に関連するデバッグ タスクと、対応するヘルプ ページへのリンクの一覧です。  
  
|||  
|-|-|  
|タスク|参照トピック|  
|Visual Studio プロジェクトのデバッグの開始、プロセスへのアタッチ、コードの中止、コードのステップ実行、カーソル位置までの実行、呼び出し履歴上の関数まで実行、次に実行されるステートメントの設定、\[マイ コードのみ\] でのステップ実行、デバッグの中止、デバッグの再起動、またはデバッグされているプロセスからのデタッチを行います。|[デバッガーでのコード間の移動](/visual-studio/debugger/navigating-through-code-with-the-debugger)|  
|プログラムのデバッグ バージョンとリリース バージョンの構成を指定します。|[Debug and Release Project Configurations](http://msdn.microsoft.com/ja-jp/0440b300-0614-4511-901a-105b771b236e)|  
|開始オプション \(コマンド ライン引数、作業ディレクトリ、リモート コンピューター\) を設定します。|[NIB: How to: Set Start Options for Application Debugging](http://msdn.microsoft.com/ja-jp/ce792058-7bac-4dd6-858b-466e872687b8)|  
|デザイン時にデバッグします。|[チュートリアル : デザイン時のデバッグ](../Topic/Walkthrough:%20Debugging%20at%20Design%20Time.md)|  
|Just\-In\-Time デバッグを有効にします。Visual Studio の外部で実行中のプログラムで致命的なエラーが発生したときに、Visual Studio デバッガーを起動する機能です。|[Just\-In\-Time デバッグ](/visual-studio/debugger/just-in-time-debugging-in-visual-studio)|  
|ソース行、アセンブリ命令、および呼び出し履歴の関数のブレークポイントを設定します。  条件、ヒット カウント、および実行位置を指定します。|[ブレークポイントの使用](/visual-studio/debugger/using-breakpoints)|  
  
## 例外処理  
 次の表は、例外処理に関連するデバッグ タスクと、対応するヘルプ ページへのリンクの一覧です。  
  
|||  
|-|-|  
|タスク|参照項目|  
|未処理の例外の発生時に中断します。|[方法 : ユーザーに処理されない例外で中断する](../Topic/How%20to:%20Break%20on%20User-Unhandled%20Exceptions.md)|  
|例外がスローされたときに中断します。|[方法 : 例外がスローされたときに中断する](../Topic/How%20to:%20Break%20When%20an%20Exception%20is%20Thrown.md)|  
|初回例外で中断します。|[方法 : 例外がスローされたときに中断する](../Topic/How%20to:%20Break%20When%20an%20Exception%20is%20Thrown.md)|  
|例外処理アシスタントを使用します。|[How to: Correct Run\-Time Errors with the Exception Assistant](../Topic/How%20to:%20Correct%20Run-Time%20Errors%20with%20the%20Exception%20Assistant.md)|  
|新しい例外を追加します。|[方法 : 新しい例外を追加する](../Topic/How%20to:%20Add%20New%20Exceptions.md)|  
|例外がスローされた後で実行を継続します。|[例外後の実行の継続](/visual-studio/debugger/continuing-execution-after-an-exception)|  
  
## エディット コンティニュ  
 次の表は、エディット コンティニュに関連するデバッグ タスクと、対応するヘルプ ページへのリンクの一覧です。  
  
|||  
|-|-|  
|タスク|参照項目|  
|エディット コンティニュのオフとオンを切り替えます。|[方法 : エディット コンティニュを有効および無効にする](../Topic/How%20to:%20Enable%20and%20Disable%20Edit%20and%20Continue.md)|  
|エディット コンティニュによるコード変更の適用を停止します。|[方法 : コード変更を中断する](../Topic/How%20to:%20Stop%20Code%20Changes.md)|  
|中断モードで編集を適用します。|[方法 : エディット コンティニュの中断モード時に編集を適用する](../Topic/How%20to:%20Apply%20Edits%20in%20Break%20Mode%20with%20Edit%20and%20Continue.md)|  
  
## デバッグ データの調査  
 次の表は、デバッグ データの表示に関連するデバッグ タスクと、対応するヘルプ ページへのリンクの一覧です。  
  
|||  
|-|-|  
|タスク|参照項目|  
|**\[レジスタ\]** ウィンドウを使用して、レジスタの内容を表示します。|[方法: \[レジスタ\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Registers%20Window.md)|  
|**\[呼び出し履歴\]** ウィンドウを使用して、現在呼び出し履歴にある関数呼び出しやプロシージャ呼び出しを表示します。|[方法 : \[呼び出し履歴\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Call%20Stack%20Window.md)|  
|**\[逆アセンブリ\]** ウィンドウを使用して、コンパイラによって作成された命令に対応するアセンブリ コードを表示します。|[方法 : \[逆アセンブル\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Disassembly%20Window.md)|  
|**\[モジュール\]** ウィンドウを使用して、プログラムが使用しているモジュールの一覧とその説明を表示します。|[方法 : \[モジュール\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Modules%20Window.md)|  
|**\[スクリプト エクスプローラー\]** ウィンドウを使用して、現在プログラムに読み込まれているスクリプト ファイルの一覧を示します。|[方法 : スクリプト ドキュメントを表示する](../Topic/How%20to:%20View%20Script%20Documents.md)|  
|**\[スレッド\]** ウィンドウを使用して、プログラムのスレッドをチェックおよび制御します。|[方法 : \[スレッド\] ウィンドウを使用する](../Topic/How%20to:%20Use%20the%20Threads%20Window.md)|  
  
## 参照  
 [チュートリアル : Windows フォームのデバッグ](../Topic/Walkthrough:%20Debugging%20a%20Windows%20Form.md)   
 [マネージ コードのデバッグ](/visual-studio/debugger/debugging-managed-code)   
 [ネイティブ コードのデバッグ](/visual-studio/debugger/debugging-native-code)   
 [Web アプリケーションとスクリプトのデバッグ](/visual-studio/debugger/debugging-web-applications-and-script)   
 [デバッグ用ユーザー インターフェイス リファレンス](/visual-studio/debugger/debugging-user-interface-reference)   
 [デバッグの設定と準備](/visual-studio/debugger/debugger-settings-and-preparation)   
 [デバッガーの基本事項](/visual-studio/debugger/debugger-basics)   
 [デバッガーでのコード間の移動](/visual-studio/debugger/navigating-through-code-with-the-debugger)   
 [IntelliTrace の使用](/visual-studio/debugger/intellitrace)   
 [C\#、F\#、および Visual Basic のプロジェクト](../Topic/Debugging%20Preparation:%20C%23,%20F%23,%20and%20Visual%20Basic%20Project%20Types.md)   
 [方法 : エディット コンティニュの中断モード時に編集を適用する](../Topic/How%20to:%20Apply%20Edits%20in%20Break%20Mode%20with%20Edit%20and%20Continue.md)