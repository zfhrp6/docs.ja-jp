---
title: WebBrowser コントロールの概要
ms.date: 03/30/2017
f1_keywords:
- WebBrowser
helpviewer_keywords:
- WebBrowser control [Windows Forms], about
- Web pages [Windows Forms], displaying in applications
ms.assetid: 6e3e1cc2-9c48-4136-9659-e99e4e60b7e9
ms.openlocfilehash: 2e69b71b3e354101d950d6f7011b13fc7c0de030
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540993"
---
# <a name="webbrowser-control-overview"></a>WebBrowser コントロールの概要
<xref:System.Windows.Forms.WebBrowser>コントロールは、WebBrowser ActiveX コントロールのマネージ ラッパーを提供します。 マネージ ラッパーを使用して、Windows フォーム クライアント アプリケーションで Web ページを表示できます。 使用することができます、<xref:System.Windows.Forms.WebBrowser>したりするアプリケーションで Internet Explorer Web ブラウズの機能を複製するコントロールが既定の Internet Explorer の機能を無効にしてとして単純な HTML ドキュメント ビューアー コントロールを使用します。 DHTML ベースのユーザー インターフェイス要素をフォームに追加しでホストされているという事実を非表示にする、コントロールを使用することも、<xref:System.Windows.Forms.WebBrowser>コントロール。 この方法では、Web コントロールを 1 つのアプリケーションで Windows フォーム コントロールとシームレスに結合することができます。  
  
## <a name="frequently-used-properties-methods-and-events"></a>よく使用されるプロパティ、メソッド、およびイベント  
 <xref:System.Windows.Forms.WebBrowser>コントロールがいくつかのプロパティ、メソッド、および Internet Explorer でのコントロールを実装に使用できるイベントです。 たとえば、使用することができます、 `Navigate` 、アドレス バーを実装するメソッド、および`GoBack`、 `GoForward`、 `Stop`、および`Refresh`ツールバーにあるナビゲーション ボタンを実装するメソッド。 処理することができます、`Navigated`の値は、アドレス バーを更新するイベント、`Url`プロパティとタイトル バーの値と、`DocumentTitle`プロパティです。  
  
 アプリケーション内で独自のページ コンテンツを生成する場合は、設定、`DocumentText`プロパティです。 現在の Web ページの内容を操作する場合は、HTML ドキュメント オブジェクト モデル (DOM) に慣れてもことができます、`Document`プロパティです。 このプロパティを格納でき、ファイル間を移動する代わりに、メモリ内のドキュメントを変更できます。  
  
 `Document`プロパティでは Web ページのクライアント アプリケーション コードからコードをスクリプトで実装されているメソッドを呼び出すこともできます。 スクリプト コードから、クライアント アプリケーション コードにアクセスするには、設定、`ObjectForScripting`プロパティです。 指定したオブジェクトとして、スクリプト コードでアクセスできる、`window.external`オブジェクト。  
  
|名前|説明|  
|----------|-----------------|  
|<xref:System.Windows.Forms.WebBrowser.Document%2A> プロパティ|現在の Web ページの HTML ドキュメント オブジェクト モデル (DOM) への管理アクセスを提供するオブジェクトを取得します。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentCompleted> イベント|Web ページには、読み込みが完了したときに発生します。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentText%2A> プロパティ|取得または HTML を現在の Web ページのコンテンツに設定します。|  
|<xref:System.Windows.Forms.WebBrowser.DocumentTitle%2A> プロパティ|現在の Web ページのタイトルを取得します。|  
|<xref:System.Windows.Forms.WebBrowser.GoBack%2A> メソッド|履歴に前のページに移動します。|  
|<xref:System.Windows.Forms.WebBrowser.GoForward%2A> メソッド|履歴に次のページに移動します。|  
|<xref:System.Windows.Forms.WebBrowser.Navigate%2A> メソッド|指定された URL に移動します。|  
|<xref:System.Windows.Forms.WebBrowser.Navigating> イベント|ナビゲーションが開始されると、キャンセルの動作を有効にする前に発生します。|  
|<xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> プロパティ|取得または Web ページのスクリプト コードは、アプリケーションを使用して通信するために使用できるオブジェクトを設定します。|  
|<xref:System.Windows.Forms.WebBrowser.Print%2A> メソッド|現在の Web ページを印刷します。|  
|<xref:System.Windows.Forms.WebBrowser.Refresh%2A> メソッド|現在の Web ページを再読み込みします。|  
|<xref:System.Windows.Forms.WebBrowser.Stop%2A> メソッド|現在のナビゲーションを停止し、音声とアニメーションなどの動的なページの要素を停止します。|  
|<xref:System.Windows.Forms.WebBrowser.Url%2A> プロパティ|取得または現在の Web ページの URL を設定します。 このプロパティを設定すると、新しい URL にコントロールが移動します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserDocumentCompletedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserEncryptionLevel>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatedEventHandler>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventArgs>  
 <xref:System.Windows.Forms.WebBrowserNavigatingEventHandler>  
 <xref:System.Windows.Forms.WebBrowserProgressChangedEventArgs>  
 <xref:System.Windows.Forms.WebBrowserReadyState>  
 <xref:System.Windows.Forms.WebBrowserRefreshOption>  
 [方法: WebBrowser コントロールで URL に移動する](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [方法: WebBrowser コントロールを使用して印刷する](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)  
 [方法: Windows フォーム アプリケーションに Web ブラウザーの機能を追加する](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md)  
 [方法: Windows フォーム アプリケーションで HTML ドキュメントビューアーを作成する](../../../../docs/framework/winforms/controls/how-to-create-an-html-document-viewer-in-a-windows-forms-application.md)  
 [方法: DHTML コードとクライアント アプリケーション コード間の双方向の通信を実装する](../../../../docs/framework/winforms/controls/implement-two-way-com-between-dhtml-and-client.md)  
 [WebBrowser セキュリティ](../../../../docs/framework/winforms/controls/webbrowser-security.md)
