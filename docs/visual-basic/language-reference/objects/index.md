---
title: "Objects (Visual Basic) | Microsoft Docs"
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
  - "objects [Visual Basic]"
ms.assetid: 651c73e4-dca8-402b-9c6b-e3902b3a3f4b
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Objects (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ここでは、Visual Basic のランタイム オブジェクトについて説明し、それぞれのメンバー プロシージャ、プロパティ、およびイベントの表を示す他のトピックへのリンクを紹介します。  
  
## Visual Basic のランタイム オブジェクト  
  
|||  
|-|-|  
|<xref:Microsoft.VisualBasic.Collection>|関連のある項目のグループを単一のオブジェクトとして参照できる便利な方法を提供します。|  
|<xref:Microsoft.VisualBasic.Information.Err%2A>|Err オブジェクトは、ランタイム エラーに関する情報を保有しています。|  
|`My.Application` オブジェクトは、次のクラスで構成されます。<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> は、すべてのプロジェクトで使用できるメンバーを提供します。<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> は、Windows フォーム アプリケーションで使用できるメンバーを提供します。<br /><br /> <xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> には、コンソール アプリケーションで使用できるメンバーを提供します。|現在のアプリケーションまたは DLL にのみ関連付けられるデータを提供します。  `My.Application` を使ってシステム レベルの情報を変更することはできません。<br /><br /> 一部のメンバーについては、Windows フォーム アプリケーションまたはコンソール アプリケーションでのみ利用できます。|  
|`My.Application.Info` \(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Info%2A>\)|バージョン番号、説明、読み込まれたアセンブリなど、アプリケーションに関する情報を取得するためのプロパティを提供します。|  
|`My.Application.Log` \(<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>\)|イベントと例外の情報を作成するためのプロパティとメソッドを、アプリケーション ログのリスナーに提供します。|  
|`My.Computer` \(<xref:Microsoft.VisualBasic.Devices.Computer>\)|オーディオ、時計、キーボード、ファイル システムなどのコンピューター コンポーネントを操作するためのプロパティを提供します。|  
|`My.Computer.Audio` \(<xref:Microsoft.VisualBasic.Devices.Audio>\)|サウンドを再生するためのメソッドを提供します。|  
|`My.Computer.Clipboard` \(<xref:Microsoft.VisualBasic.Devices.Computer.Clipboard%2A>\)|クリップボードを操作するためのメソッドを提供します。|  
|`My.Computer.Clock` \(<xref:Microsoft.VisualBasic.Devices.Clock>\)|システム時計から現在の現地時刻および世界協定時刻 \(グリニッジ標準時と同じ\) にアクセスするためのプロパティを提供します。|  
|`My.Computer.FileSystem` \(<xref:Microsoft.VisualBasic.FileIO.FileSystem>\)|ドライブ、ファイル、およびディレクトリを操作するためのプロパティとメソッドを提供します。|  
|`My.Computer.FileSystem.SpecialDirectories` \(<xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>\)|頻繁に参照されるディレクトリへのアクセスに使用するプロパティを提供します。|  
|`My.Computer.Info` \(<xref:Microsoft.VisualBasic.Devices.ComputerInfo>\)|コンピューターのメモリ、読み込まれているアセンブリ、コンピューター名、オペレーティング システムなどに関する情報を取得するためのプロパティを提供します。|  
|`My.Computer.Keyboard` \(<xref:Microsoft.VisualBasic.Devices.Keyboard>\)|キーボードの現在の状態 \(現在どのキーが押されているかなど\) にアクセスするためのプロパティや、アクティブなウィンドウにキーストロークを送るためのメソッドが用意されています。|  
|`My.Computer.Mouse` \(<xref:Microsoft.VisualBasic.Devices.Mouse>\)|ローカル コンピューターにインストールされたマウスの形式や構成に関する情報を取得するためのプロパティを提供します。|  
|`My.Computer.Network` \(<xref:Microsoft.VisualBasic.Devices.Network>\)|コンピューターの接続先ネットワークと対話するためのプロパティ、イベント、およびメソッドを提供します。|  
|`My.Computer.Ports` \(<xref:Microsoft.VisualBasic.Devices.Ports>\)|コンピューターのシリアル ポートにアクセスするためのプロパティおよびメソッドを提供します。|  
|`My.Computer.Registry` \(<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>\)|レジストリを操作するプロパティとメソッドを提供します。|  
|[My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)|現在のプロジェクト内で宣言されている各 Windows フォームのインスタンスにアクセスするためのプロパティを提供します。|  
|`My.Log` \(<xref:Microsoft.VisualBasic.Logging.AspLog>\)|イベントと例外の情報を作成するためのプロパティとメソッドを、Web アプリケーションのログ リスナーに提供します。|  
|[My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)|要求されたページに対する <xref:System.Web.HttpRequest> オブジェクトを取得します。  `My.Request` オブジェクトには現在の HTTP 要求に関する情報が含まれます。<br /><br /> `My.Request` オブジェクトは [!INCLUDE[vstecasp](../../../visual-basic/developing-apps/programming/drives-directories-files/includes/vstecasp_md.md)] アプリケーションでのみ利用できます。|  
|[My.Resources Object](../../../visual-basic/language-reference/objects/my-resources-object.md)|アプリケーションのリソースにアクセスするためのプロパティとクラスを提供します。|  
|[My.Response Object](../../../visual-basic/language-reference/objects/my-response-object.md)|<xref:System.Web.UI.Page> に関連付けられている <xref:System.Web.HttpResponse> オブジェクトを取得します。  このオブジェクトを使用することにより、HTTP 応答データをクライアントに送り、この応答に関する情報を格納できます。<br /><br /> `My.Response` オブジェクトは [!INCLUDE[vstecasp](../../../visual-basic/developing-apps/programming/drives-directories-files/includes/vstecasp_md.md)] アプリケーションでのみ利用できます。|  
|[My.Settings Object](../../../visual-basic/language-reference/objects/my-settings-object.md)|アプリケーションの設定値にアクセスするためのプロパティとメソッドを提供します。|  
|`My.User` \(<xref:Microsoft.VisualBasic.ApplicationServices.User>\)|現在のユーザーに関する情報へのアクセスを提供します。|  
|[My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)|現在のプロジェクトから参照される各 Web サービスの単一のインスタンスを作成し、それらにアクセスするためのプロパティを提供します。|  
|<xref:Microsoft.VisualBasic.FileIO.TextFieldParser>|構造化テキスト ファイルの解析に使用するメソッドとプロパティを提供します。|  
  
## 参照  
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)   
 [Visual Basic](../../../visual-basic/index.md)