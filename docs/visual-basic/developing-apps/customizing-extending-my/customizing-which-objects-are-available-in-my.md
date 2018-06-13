---
title: My で利用可能なオブジェクトのカスタマイズ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
ms.openlocfilehash: b06e71784a4d02bcbcd755d14e57ef88c4322f7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592159"
---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>My で利用可能なオブジェクトのカスタマイズ (Visual Basic)
このトピックでは、これを制御する方法について説明`My`するには、プロジェクトのオブジェクトが有効になって`_MYTYPE`条件付きコンパイル定数。 Visual Studio 統合開発環境 (IDE) の保持、`_MYTYPE`プロジェクトとプロジェクトの種類の同期の条件付きコンパイル定数。  
  
## <a name="predefined-mytype-values"></a>定義済み _MYTYPE 値  
 使用する必要があります、`/define`コンパイラ オプションを設定する、`_MYTYPE`条件付きコンパイル定数。 独自の値を指定するときに、`_MYTYPE`定数、文字列値で囲みますバック スラッシュ/引用符 (\\") のシーケンス。 たとえば、次のように使用する可能性があります。  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 この表ではどのような`_MYTYPE`条件付きコンパイル定数に設定されているいくつかのプロジェクト タイプ用。  
  
|プロジェクトの種類|_MYTYPE 値|  
|------------------|--------------------|  
|クラス ライブラリ|"Windows"|  
|コンソール アプリケーション|"Console"|  
|Web|"Web"|  
|Web コントロール ライブラリ|"WebControl"|  
|Windows アプリケーション|"WindowsForms"|  
|カスタムの開始時に、Windows アプリケーション `Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Windows コントロール ライブラリ|"Windows"|  
|Windows サービス|"Console"|  
|Empty|"Empty"|  
  
> [!NOTE]
>  すべての条件付きコンパイルの文字列比較では関係なく、大文字小文字が区別`Option Compare`ステートメントを設定します。  
  
## <a name="dependent-my-compilation-constants"></a>_MY コンパイル定数  
 `_MYTYPE`条件付きコンパイル定数は、他のいくつかの値をさらに、制御`_MY`コンパイル定数。  
  
|_MYTYPE|_MYAPPLICATIONTYPE|_MYCOMPUTERTYPE|_MYFORMS|_MYUSERTYPE|_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|"Console"|"Console"|"Windows"|未定義|"Windows"|true|  
|"Custom"|未定義|未定義|未定義|未定義|未定義|  
|"Empty"|未定義|未定義|未定義|未定義|未定義|  
|"Web"|未定義|"Web"|false|"Web"|false|  
|"WebControl"|未定義|"Web"|false|"Web"|true|  
|"Windows"または""|"Windows"|"Windows"|未定義|"Windows"|TRUE|  
|"WindowsForms"|"WindowsForms"|"Windows"|true|"Windows"|true|  
|"WindowsFormsWithCustomSubMain"|"Console"|"Windows"|true|"Windows"|true|  
  
 既定では、未定義の条件付きコンパイル定数を解決する`FALSE`です。 既定の動作を上書きするようにプロジェクトをコンパイルするときに、未定義の定数の値を指定できます。  
  
> [!NOTE]
>  ときに`_MYTYPE`設定されているプロジェクトに含まれる"Custom"に、`My`が名前空間が含まれていないオブジェクトにはです。 ただし、設定`_MYTYPE`を追加できない、"Empty"のように、コンパイラ、`My`名前空間とそのオブジェクト。  
  
 このテーブルの定義済みの値の効果の説明、`_MY`コンパイル定数。  
  
|定数|説明|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|により、`My.Application`定数は、「コンソールで、」Windows"または"WindowsForms"。<br /><br /> -派生した"Console"バージョン<xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>します。 "Windows"のバージョンよりも少ないメンバーがあります。<br />-派生した"Windows"バージョン<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>参照できますが、"WindowsForms"バージョンよりも少ないメンバー。<br />-の"WindowsForms"バージョン`My.Application`から派生した<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>です。 場合、 `TARGET` "winexe"である定数を定義し、クラスが含まれています、`Sub Main`メソッドです。|  
|`_MYCOMPUTERTYPE`|により、`My.Computer`定数が"Web"または"Windows"の場合。<br /><br /> 、派生して"Web"バージョン<xref:Microsoft.VisualBasic.Devices.ServerComputer>、"Windows"のバージョンよりも少ないメンバーを持つとします。<br />-場合は、、"Windows"バージョン`My.Computer`から派生した<xref:Microsoft.VisualBasic.Devices.Computer>です。|  
|`_MYFORMS`|により、`My.Forms`定数の場合、`TRUE`です。|  
|`_MYUSERTYPE`|により、`My.User`定数が"Web"または"Windows"の場合。<br /><br /> -の"Web"バージョン`My.User`の現在の HTTP 要求のユーザー id に関連付けられています。<br />-場合は、、"Windows"バージョン`My.User`スレッドの現在のプリンシパルに関連付けられています。|  
|`_MYWEBSERVICES`|により、`My.WebServices`定数の場合、`TRUE`です。|  
|`_MYTYPE`|により、 `My.Log`、 `My.Request`、および`My.Response`定数が"Web"である場合、します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.Logging.Log>  
 <xref:Microsoft.VisualBasic.ApplicationServices.User>  
 [プロジェクトの種類に応じた My の機能](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [My.Forms オブジェクト](../../../visual-basic/language-reference/objects/my-forms-object.md)  
 [My.Request オブジェクト](../../../visual-basic/language-reference/objects/my-request-object.md)  
 [My.Response オブジェクト](../../../visual-basic/language-reference/objects/my-response-object.md)  
 [My.WebServices オブジェクト](../../../visual-basic/language-reference/objects/my-webservices-object.md)
