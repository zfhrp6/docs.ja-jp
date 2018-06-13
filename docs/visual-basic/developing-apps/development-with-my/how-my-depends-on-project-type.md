---
title: プロジェクトの種類に応じた My の機能 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- _MYTYPE
ms.assetid: c188b38e-bd9d-4121-9983-41ea6a94d28e
ms.openlocfilehash: d196309bb2780db757515bd6ba1927c5821e2475
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592081"
---
# <a name="how-my-depends-on-project-type-visual-basic"></a>プロジェクトの種類に応じた My の機能 (Visual Basic)
`My` 特定のプロジェクトの種類で必要なオブジェクトのみを公開します。 たとえば、`My.Forms`オブジェクトは、Windows フォーム アプリケーションで使用できますが、コンソール アプリケーションでは使用できません。 このトピックの内容を説明する`My`オブジェクトは、異なる種類のプロジェクトで使用できます。  
  
## <a name="my-in-windows-applications-and-web-sites"></a>自分の Windows アプリケーションや Web サイト  
 `My` 現在、プロジェクトの種類に便利なオブジェクトのみを公開します。適用されないオブジェクトを抑制します。 たとえば、次の図は、 `My` Windows フォーム プロジェクトでのオブジェクト モデルです。  
  
 ![図形の Windows フォーム アプリケーションで](../../../visual-basic/developing-apps/development-with-my/media/myinwinform.png "MyInWinForm")  
  
 Web サイト プロジェクトで`My`Web 開発者に関連するオブジェクトを公開 (など、`My.Request`と`My.Response`オブジェクト)、関連するではないオブジェクトを制限しながら (など、`My.Forms`オブジェクト)。 次の図は、 `My` Web サイト プロジェクトのオブジェクト モデル。  
  
 ![図形の Web アプリケーションで](../../../visual-basic/developing-apps/development-with-my/media/myinweb.png "MyInWeb")  
  
## <a name="project-details"></a>プロジェクトの詳細  
 次の表では`My`8 プロジェクトの種類のオブジェクトが既定で有効にします。 Windows アプリケーション、クラス ライブラリ、コンソール アプリケーション、Windows コントロール ライブラリ、Web コントロール ライブラリ、Windows サービス、空、および Web サイトです。  
  
 3 つのバージョンがある、`My.Application`オブジェクト、2 つのバージョン、`My.Computer`オブジェクト、および 2 つのバージョンの`My.User`オブジェクトです。 これらのバージョンに関する詳細は、表の後に、脚注で指定します。  
  
|My オブジェクト|Windows アプリケーション|クラス ライブラリ|コンソール アプリケーション|Windows コントロール ライブラリ|Web コントロール ライブラリ|Windows サービス|Empty|Web サイト|  
|---|---|---|---|---|---|---|---|---|  
|`My.Application`|**[はい]** <sup>1</sup>|**[はい]** <sup>2</sup>|**[はい]** <sup>3</sup>|**[はい]** <sup>2</sup>|×|**[はい]** <sup>3</sup>|×|×|  
|`My.Computer`|**[はい]** <sup>4</sup>|**[はい]** <sup>4</sup>|**[はい]** <sup>4</sup>|**[はい]** <sup>4</sup>|**[はい]** <sup>5</sup>|**[はい]** <sup>4</sup>|×|**[はい]** <sup>5</sup>|  
|`My.Forms`|**はい**|×|×|**はい**|×|Ｘ|Ｘ|Ｘ|  
|`My.Log`|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|×|**はい**|  
|`My.Request`|×|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|×|**はい**|  
|`My.Resources`|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|×|Ｘ|  
|`My.Response`|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|Ｘ|×|**はい**|  
|`My.Settings`|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|×|×|  
|`My.User`|**[はい]** <sup>6</sup>|**[はい]** <sup>6</sup>|**[はい]** <sup>6</sup>|**[はい]** <sup>6</sup>|**[はい]** <sup>7</sup>|**[はい]** <sup>6</sup>|×|**[はい]** <sup>7</sup>|  
|`My.WebServices`|**はい**|**はい**|**はい**|**はい**|**はい**|**はい**|×|×|  
  
 <sup>1</sup> Windows フォームのバージョンの`My.Application`します。 コンソールのバージョンから派生した (注 3 を参照してください)。アプリケーションの windows と対話するためのサポートを追加し、Visual Basic アプリケーション モデルを提供します。  
  
 <sup>2</sup>ライブラリ版の`My.Application`します。 アプリケーションで必要な基本的な機能を提供します: アプリケーション ログに書き込むと、アプリケーションの情報にアクセスするメンバーを提供します。  
  
 <sup>3</sup>コンソールのバージョンの`My.Application`します。 ライブラリのバージョンからの派生元 (メモ 2 を参照)、し、アプリケーションのコマンドライン引数と ClickOnce 配置の情報にアクセスするための追加メンバーを追加します。  
  
 <sup>4</sup> Windows 版の`My.Computer`します。 サーバーのバージョンからの派生元 (メモ 5 を参照)、し、キーボード、画面、およびマウスなどのクライアント コンピューターで役に立つオブジェクトへのアクセスを提供します。  
  
 <sup>5</sup>のサーバー バージョン`My.Computer`します。 名前、時計、およびなどへのアクセスなど、コンピューターに関する基本情報を提供します。  
  
 <sup>6</sup> Windows 版の`My.User`します。 このオブジェクトは、スレッドの現在の id に関連付けられます。  
  
 <sup>7</sup>の web バージョン`My.User`します。 このオブジェクトは、アプリケーションの現在の HTTP 要求のユーザー id に関連付けられます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.Logging.Log>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [My で利用可能なオブジェクトのカスタマイズ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [My.Forms オブジェクト](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [My.Request オブジェクト](../../../visual-basic/language-reference/objects/my-request-object.md)  
 [My.Response オブジェクト](../../../visual-basic/language-reference/objects/my-response-object.md)  
 [My.WebServices オブジェクト](../../../visual-basic/language-reference/objects/my-webservices-object.md)
