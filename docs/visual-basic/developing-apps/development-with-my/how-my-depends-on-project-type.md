---
title: "どのように私はプロジェクトの種類 (Visual Basic) に依存します |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: d193dade94980f04b31605ea6fa968f9fa7d0ad6
ms.lasthandoff: 03/13/2017

---
# <a name="how-my-depends-on-project-type-visual-basic"></a>プロジェクトの種類に応じた My の機能 (Visual Basic)
`My`特定のプロジェクトの種類で必要なオブジェクトのみを公開します。 たとえば、`My.Forms`オブジェクトは、Windows フォーム アプリケーションで使用できますが、コンソール アプリケーションでは使用できません。 このトピックを説明する`My`オブジェクトは、異なる種類のプロジェクトで使用できます。  
  
## <a name="my-in-windows-applications-and-web-sites"></a>自分の Windows アプリケーションや Web サイト  
 `My`現在、プロジェクトの種類内で使用されるオブジェクトのみを公開します。適用されないオブジェクトを抑制します。 たとえば、次の図は、 `My` Windows フォーム プロジェクトのオブジェクト モデルです。  
  
 ![図形の Windows フォーム アプリケーションで](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 Web サイト プロジェクトで`My`Web 開発者に関連するオブジェクトを公開 (など、`My.Request`と`My.Response`オブジェクト)、関連性の低いオブジェクト制限しながら (など、`My.Forms`オブジェクト)。 次の図は、 `My` Web サイト プロジェクトのオブジェクト モデル。  
  
 ![図形の Web アプリケーションで](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>プロジェクトの詳細  
 次の表では`My`8 プロジェクトの種類のオブジェクトが既定で有効にします。 Windows アプリケーション、クラス ライブラリ、コンソール アプリケーション、Windows コントロール ライブラリ、Web コントロール ライブラリ、Windows サービス、空白、および Web サイトです。  
  
 次の&3; つのバージョンがある、`My.Application`オブジェクト、2 つのバージョン、`My.Computer`オブジェクト、および&2; つのバージョンの`My.User`オブジェクトの詳細については、これらのバージョンは、表の脚注で指定します。  
  
|My オブジェクト|Windows アプリケーション|クラス ライブラリ|コンソール アプリケーション|Windows コントロール ライブラリ|Web コントロール ライブラリ|Windows サービス|Empty|Web サイト|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**Yes** <sup>1</sup>|**Yes** <sup>2</sup>|**Yes** <sup>3</sup>|**Yes** <sup>2</sup>|いいえ|**Yes** <sup>3</sup>|いいえ|いいえ|  
|`My.Computer`|**Yes** <sup>4</sup>|**Yes** <sup>4</sup>|**Yes** <sup>4</sup>|**Yes** <sup>4</sup>|**Yes** <sup>5</sup>|**Yes** <sup>4</sup>|いいえ|**Yes** <sup>5</sup>|  
|`My.Forms`|**はい**|いいえ|いいえ|**はい**|いいえ|いいえ|いいえ|いいえ|  
|`My.Log`|いいえ|いいえ|いいえ|いいえ|いいえ|いいえ|いいえ|**はい**|  
|`My.Request`|いいえ|いいえ|いいえ|いいえ|いいえ|いいえ|いいえ|**はい**|  
|`My.Resources`|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|いいえ|いいえ|  
|`My.Response`|いいえ|いいえ|いいえ|いいえ|いいえ|いいえ|いいえ|**はい**|  
|`My.Settings`|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|いいえ|いいえ|  
|`My.User`|**Yes** <sup>6</sup>|**Yes** <sup>6</sup>|**Yes** <sup>6</sup>|**Yes** <sup>6</sup>|**Yes** <sup>7</sup>|**Yes** <sup>6</sup>|いいえ|**Yes** <sup>7</sup>|  
|`My.WebServices`|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|いいえ|いいえ|  
  
 <sup>1</sup> Windows フォームのバージョンの`My.Application`です。 コンソールのバージョンからの派生元 (メモ 3 を参照してください)。アプリケーションの windows を操作するためのサポートを追加し、提供、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]アプリケーション モデルです。  
  
 <sup>2</sup>ライブラリ版の`My.Application`です。 アプリケーションで必要な基本機能を提供します。 をアプリケーション ログに書き込むと、アプリケーションの情報にアクセスするメンバーを提供します。  
  
 <sup>3</sup>のバージョンのコンソール`My.Application`します。 ライブラリのバージョンからの派生元 (メモ 2 を参照)、アプリケーションのコマンドライン引数と ClickOnce 配置の情報にアクセスするための追加メンバーを追加します。  
  
 <sup>4</sup>の Windows バージョン`My.Computer`です。 サーバーのバージョンからの派生元 (メモ 5 を参照)、キーボード、画面、およびマウスなどのクライアント コンピューター上の有効なオブジェクトへのアクセスを提供します。  
  
 <sup>5</sup>のサーバー バージョン`My.Computer`です。 名前、時計、およびなどへのアクセスなど、コンピューターに関する基本情報を提供します。  
  
 <sup>6</sup>の Windows バージョン`My.User`です。 このオブジェクトは、スレッドの現在の id に関連付けられます。  
  
 <sup>7</sup>の web バージョン`My.User`です。 このオブジェクトは、アプリケーションの現在の HTTP 要求のユーザー id に関連付けられます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer></xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log></xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User></xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [利用可能なオブジェクトのカスタマイズ ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)   
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)   
 [My.Forms オブジェクト](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.Request オブジェクト](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [My.Response オブジェクト](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [My.WebServices オブジェクト](../../../visual-basic/language-reference/objects/my-webservices-object.md)
