---
title: "Visual Basic アプリケーション モデルの概要 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My.Application object, Visual Basic application model
- Visual Basic application model
ms.assetid: 17538984-84fe-43c9-82c8-724c9529fe8b
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0925bb102c148480d82128b91cbf1762de24e7ec
ms.lasthandoff: 03/13/2017

---
# <a name="overview-of-the-visual-basic-application-model"></a>Visual Basic アプリケーション モデルの概要
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows フォーム アプリケーションの動作を制御するため、適切に定義されたモデルを提供します。、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]アプリケーション モデルです。 このモデルには、アプリケーションのスタートアップおよびシャット ダウン、だけでなくハンドルされない例外をキャッチのイベントを処理するためのイベントが含まれています。 単一インスタンス アプリケーションを開発するためのサポートも提供します。 アプリケーション モデルを拡張するため、管理を必要とする開発者は、オーバーライド可能なメソッドをカスタマイズできます。  
  
## <a name="uses-for-the-application-model"></a>アプリケーション モデルの使用方法  
 一般的なアプリケーションは、起動時し、シャット ダウン時にタスクを実行する必要があります。 たとえば、起動時、アプリケーションことができますスプラッシュ画面を表示、データベース接続を作成、保存済みの状態を読み込むおよび具合です。 アプリケーションがシャット ダウンした、データベース接続を閉じて現在の状態を保存、具合およびできます。 さらに、アプリケーション コードを実行できます特定アプリケーションが終了するとき下矢印が予期せず、このような未処理の例外時のようです。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]アプリケーション モデルでは、簡単に作成、*単一インスタンス*アプリケーションです。 単一インスタンスのアプリケーションでは、コンピューターを一度に実行する通常のアプリケーションから、アプリケーションのインスタンスを&1; つだけが異なります。 単一インスタンスのアプリケーションの別のインスタンスを起動しようとすると、結果の通知を送信元のインスタンス: によって、`StartupNextInstance`イベント-別の起動試行が行われたことです。 通知には、後続のインスタンスのコマンドライン引数が含まれています。 初期化を行う前に、アプリケーションの後続のインスタンスが閉じられます。  
  
 単一インスタンス アプリケーションを起動し、最初のインスタンスまたはアプリケーションの後続のインスタンスかどうかをチェックします。  
  
-   最初のインスタンスの場合、通常どおり起動します。  
  
-   最初のインスタンスの実行中に、アプリケーションの起動に後続しようとする各と動作は異なります。 その後の試行では、コマンドライン引数の最初のインスタンスに通知し、すぐに終了します。 最初のインスタンスのハンドル、`StartupNextInstance`以降のインスタンスのコマンドライン引数を通知し、引き続き実行を決定するイベントです。  
  
     この図では、後続のインスタンスが最初のインスタンスを通知する方法を示します。  
  
     ![単一のインスタンス アプリケーション イメージ](../../../visual-basic/developing-apps/development-with-my/media/singleinstance.gif "SingleInstance")  
  
 処理することにより、`StartupNextInstance`イベント、単一インスタンス アプリケーションの動作を制御できます。 たとえば、Microsoft Outlook は通常、単一インスタンス アプリケーションとして実行します。Outlook が実行され、Outlook を起動しようとするときに再度元のインスタンスにフォーカスを移動しますが、別のインスタンスは開かれません。  
  
## <a name="events-in-the-application-model"></a>アプリケーション モデル内のイベント  
 アプリケーション モデルには、次のイベントがあります。  
  
-   **アプリケーションの起動**します。 アプリケーションが例外を<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>起動時にイベント</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>。 このイベントを処理することによって、メイン フォームが読み込まれる前に、アプリケーションを初期化するコードを追加できます。 `Startup`が必要な場合、このイベントは、また、起動プロセスのフェーズでは、そのアプリケーションの実行のキャンセルは提供します。  
  
     アプリケーションのスタートアップ コードが実行中に、スプラッシュ スクリーンを表示するアプリケーションを構成することができます。 既定では、アプリケーション モデルは、ロゴを抑制スクリーンは表示か、`/nosplash`または`-nosplash`コマンドライン引数を使用します。  
  
-   **単一インスタンス アプリケーション**します。 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>イベントは、単一インスタンスのアプリケーションの後続のインスタンスが開始されると発生します</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>。 このイベントは、後続のインスタンスのコマンドライン引数を渡します。  
  
-   **未処理の例外**します。 アプリケーションには、未処理の例外が発生すると、発生、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>イベント</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>。 そのイベントのハンドラーは、例外を確認し、実行を継続するかどうかを判断できます。  
  
     `UnhandledException`イベントは、いくつかの状況では発生しません。 詳細については、 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>。</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>を参照してください。  
  
-   **ネットワーク接続の変更**します。 アプリケーションを生成しているコンピューターのネットワークの可用性が変更された場合、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>イベント</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>。  
  
     `NetworkAvailabilityChanged`イベントは、いくつかの状況では発生しません。 詳細については、 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>。</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>を参照してください。  
  
-   **アプリケーションのシャット ダウン**します。 このアプリケーションでは、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>シャット ダウンしようとしているときに通知するイベントです</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>。 イベントのハンドラーで行うことができるために必要なアプリケーションを操作することを確認して — を終了し、保存が完了します。 メイン フォームが閉じたときをシャット ダウン、またはすべてのフォームが閉じるときにのみをシャット ダウン、アプリケーションを構成することができます。  
  
## <a name="availability"></a>可用性  
 既定では、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]アプリケーション モデルは、Windows フォーム プロジェクトで使用可能です。 異なるスタートアップ オブジェクトを使用するアプリケーションを構成したり、カスタム アプリケーション コードを開始するかどうかは`Sub Main`ですが、オブジェクト、またはクラスの実装が必要になる、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>アプリケーション モデルを使用するクラス</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>。 スタートアップ オブジェクトを変更する方法の詳細については、次を参照してください。[アプリケーション ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.StartupNextInstance>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.NetworkAvailabilityChanged>   
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>   
 [Visual Basic アプリケーション モデルの拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
