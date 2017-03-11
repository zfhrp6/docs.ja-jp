---
title: "How My Depends on Project Type (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "_MYTYPE"
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How My Depends on Project Type (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My` では、対象のプロジェクトの種類で必要なオブジェクトのみが公開されます。  たとえば、`My.Forms` オブジェクトは、Windows フォーム アプリケーションでは利用できますが、コンソール アプリケーションでは利用できません。  このトピックでは、プロジェクトの各種類でどの `My` オブジェクトを利用できるかについて説明します。  
  
## Windows アプリケーションおよび Web サイトでの My  
 `My` では、現在のプロジェクトの種類で利用できるオブジェクトのみが公開され、対象外のオブジェクトは無効になります。  たとえば、次のイメージは、Windows フォーム プロジェクトでの `My` のオブジェクト モデルを示します。  
  
 ![Windows フォーム アプリケーションでの My の形](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 Web サイト プロジェクトでは、`My` は、Web 開発者に関係するオブジェクト \(たとえば `My.Request` オブジェクトや `My.Response` オブジェクト\) は公開する一方、関係しないオブジェクト \(たとえば `My.Forms` オブジェクト\) は無効にします。  次のイメージは、Web サイト プロジェクトでの `My` のオブジェクト モデルを示します。  
  
 ![Web アプリケーションでの My の形](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## プロジェクトの詳細  
 次の表は、8 つのプロジェクトの種類 \(Windows アプリケーション、クラス ライブラリ、コンソール アプリケーション、Windows コントロール ライブラリ、Web コントロール ライブラリ、Windows サービス、空のプロジェクト、および Web サイト\) において、どの `My` オブジェクトが既定で有効になっているかを示します。  
  
 `My.Application` オブジェクトには 3 つのバージョンがあり、`My.Computer` オブジェクトと `My.User` オブジェクトにはそれぞれ 2 つのバージョンがあります。各バージョンの詳細については、表の後の脚注で説明します。  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|My オブジェクト|Windows アプリケーション|クラス ライブラリ|コンソール アプリケーション|Windows コントロール ライブラリ|Web コントロール ライブラリ|Windows サービス|空|Web サイト|  
|`My.Application`|**○** <sup>1</sup>|**○** <sup>2</sup>|**○** <sup>3</sup>|**○** <sup>2</sup>|Ｘ|**○** <sup>3</sup>|Ｘ|Ｘ|  
|`My.Computer`|**○** <sup>4</sup>|**○** <sup>4</sup>|**○** <sup>4</sup>|**○** <sup>4</sup>|**○** <sup>5</sup>|**○** <sup>4</sup>|Ｘ|**○** <sup>5</sup>|  
|`My.Forms`|**○**|Ｘ|Ｘ|**○**|Ｘ|Ｘ|Ｘ|Ｘ|  
|`My.Log`|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|**○**|  
|`My.Request`|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|**○**|  
|`My.Resources`|**○**|**○**|**○**|**○**|**○**|**○**|Ｘ|Ｘ|  
|`My.Response`|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|**○**|  
|`My.Settings`|**○**|**○**|**○**|**○**|**○**|**○**|Ｘ|Ｘ|  
|`My.User`|**○** <sup>6</sup>|**○** <sup>6</sup>|**○** <sup>6</sup>|**○** <sup>6</sup>|**○** <sup>7</sup>|**○** <sup>6</sup>|Ｘ|**○** <sup>7</sup>|  
|`My.WebServices`|**○**|**○**|**○**|**○**|**○**|**○**|Ｘ|Ｘ|  
  
 <sup>1</sup> `My.Application` の Windows フォーム バージョンです。  コンソール バージョン \(注 3 を参照\) から派生されています。アプリケーションのウィンドウとのやり取りのサポートが追加され、また [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] アプリケーション モデルが備わっています。  
  
 <sup>2</sup> `My.Application` のライブラリ バージョンです。  アプリケーションが必要とする基本機能が備わっており、アプリケーション ログへの書き込みや、アプリケーション情報へのアクセスのためのメンバーが用意されています。  
  
 <sup>3</sup> `My.Application` のコンソール バージョンです。  ライブラリ バージョン \(注 2 を参照\) から派生され、アプリケーションのコマンド ライン引数や ClickOnce 配置情報にアクセスするためのメンバーが加わっています。  
  
 <sup>4</sup> `My.Computer` の Windows バージョンです。  サーバー バージョン \(注 5 を参照\) から派生され、クライアント マシンで有用なオブジェクト \(キーボード、画面、マウスなど\) にアクセスできます。  
  
 <sup>5</sup> `My.Computer` のサーバー バージョンです。  名前や時計へのアクセスなど、コンピューターについての基本情報が備わっています。  
  
 <sup>6</sup> `My.User` の Windows バージョンです。  このオブジェクトは、スレッドの現在の ID と関連付けられています。  
  
 <sup>7</sup> `My.User` の Web バージョンです。  このオブジェクトは、アプリケーションの現在の HTTP 要求のユーザー ID と関連付けられています。  
  
## 参照  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [Customizing Which Objects are Available in My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [\/define](../../../visual-basic/reference/command-line-compiler/define.md)   
 [My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [My.Response Object](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md)