---
title: "(Visual Basic) で利用可能なオブジェクトのカスタマイズ |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- My namespace, customizing
- My namespace
ms.assetid: 4e8279c2-ed5b-4681-8903-8a6671874000
caps.latest.revision: 12
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
ms.openlocfilehash: 6791398270e4348adf356eb36a385bfbefde873c
ms.lasthandoff: 03/13/2017

---
# <a name="customizing-which-objects-are-available-in-my-visual-basic"></a>My で利用可能なオブジェクトのカスタマイズ (Visual Basic)
このトピックでは、これを制御する方法について説明`My`するには、プロジェクトのオブジェクトが有効になっている`_MYTYPE`条件付きコンパイル定数です。 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]統合開発環境 (IDE) の維持、`_MYTYPE`プロジェクト、プロジェクトの種類との同期の条件付きコンパイル定数です。  
  
## <a name="predefined-mytype-values"></a>定義済み _MYTYPE 値  
 使用する必要があります、`/define`コンパイラ オプションを設定する、`_MYTYPE`条件付きコンパイル定数です。 値を指定するときに、`_MYTYPE`一定で囲む必要があります文字列値にバック スラッシュ/引用符 (\\") のシーケンス。 たとえば、次のように使用する可能性があります。  
  
```  
/define:_MYTYPE=\"WindowsForms\"  
```  
  
 次の表はどのような`_MYTYPE`いくつかのプロジェクトの種類には、条件付きコンパイル定数に設定します。  
  
|プロジェクトの種類|_MYTYPE 値|  
|------------------|--------------------|  
|クラス ライブラリ|"Windows"|  
|コンソール アプリケーション|「コンソール」|  
|Web|"Web"|  
|Web コントロール ライブラリ|"WebControl"|  
|Windows アプリケーション|"WindowsForms"|  
|定義したカスタムの開始時に、Windows アプリケーション`Sub Main`|"WindowsFormsWithCustomSubMain"|  
|Windows コントロール ライブラリ|"Windows"|  
|Windows サービス|「コンソール」|  
|Empty|"Empty"|  
  
> [!NOTE]
>  すべての条件付きコンパイルの文字列比較は関係なく、大文字小文字が区別`Option Compare`ステートメントを設定します。  
  
## <a name="dependent-my-compilation-constants"></a>_MY コンパイル定数  
 `_MYTYPE`条件付きコンパイル定数は、その他のいくつかの値をさらに制御`_MY`コンパイル定数。  
  
|_MYTYPE|_MYAPPLICATIONTYPE|_MYCOMPUTERTYPE|_MYFORMS|_MYUSERTYPE|_MYWEBSERVICES|  
|--------------|-------------------------|----------------------|---------------|------------------|---------------------|  
|「コンソール」|「コンソール」|"Windows"|未定義|"Windows"|TRUE|  
|"Custom"|未定義|未定義|未定義|未定義|未定義|  
|"Empty"|未定義|未定義|未定義|未定義|未定義|  
|"Web"|未定義|"Web"|FALSE|"Web"|FALSE|  
|"WebControl"|未定義|"Web"|FALSE|"Web"|TRUE|  
|"Windows"または""|"Windows"|"Windows"|未定義|"Windows"|TRUE|  
|"WindowsForms"|"WindowsForms"|"Windows"|TRUE|"Windows"|TRUE|  
|"WindowsFormsWithCustomSubMain"|「コンソール」|"Windows"|TRUE|"Windows"|TRUE|  
  
 既定では、未定義の条件付きコンパイル定数を解決する`FALSE`です。 既定の動作をオーバーライドするようにプロジェクトをコンパイルするときに、未定義の定数の値を指定できます。  
  
> [!NOTE]
>  `_MYTYPE`設定されているプロジェクトに含まれる"Custom"に、`My`名前空間が含まれていないオブジェクトにはです。 ただし、設定`_MYTYPE`に「空の」コンパイラが追加できないように、`My`名前空間とそのオブジェクト。  
  
 このテーブルの定義済みの値の効果の説明、`_MY`コンパイル定数です。  
  
|定数|説明|  
|--------------|-------------|  
|`_MYAPPLICATIONTYPE`|により、`My.Application`定数は、「コンソールで、」Windows"または"WindowsForms"。<br /><br /> -「コンソール」のバージョンが<xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>。</xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase>から派生します。 "Windows"バージョンよりも少ないメンバーです。<br />派生して"Windows"バージョン<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>そして"WindowsForms"バージョンよりも少ないメンバーを持つ</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>。<br />-"WindowsForms"バージョンの`My.Application` <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>から派生 場合、`TARGET`する「ため」定数が定義し、このクラスは、`Sub Main`メソッドです。|  
|`_MYCOMPUTERTYPE`|により、`My.Computer`定数が"Web"または"Windows"の場合。<br /><br /> -派生した"Web"バージョン<xref:Microsoft.VisualBasic.Devices.ServerComputer>、"Windows"バージョンよりも少ないメンバーを持つとします</xref:Microsoft.VisualBasic.Devices.ServerComputer>。<br />-の"Windows"バージョン`My.Computer` <xref:Microsoft.VisualBasic.Devices.Computer>.</xref:Microsoft.VisualBasic.Devices.Computer>から派生|  
|`_MYFORMS`|により、`My.Forms`定数の場合、`TRUE`です。|  
|`_MYUSERTYPE`|により、`My.User`定数が"Web"または"Windows"の場合。<br /><br /> -の"Web"バージョン`My.User`現在の HTTP 要求のユーザー id に関連付けられています。<br />-の"Windows"バージョン`My.User`スレッドの現在のプリンシパルに関連付けられています。|  
|`_MYWEBSERVICES`|により、`My.WebServices`定数の場合、`TRUE`です。|  
|`_MYTYPE`|により、 `My.Log`、 `My.Request`、および`My.Response`定数は、"Web"場合は、です。|  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase>   
 <xref:Microsoft.VisualBasic.Devices.Computer></xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.Logging.Log></xref:Microsoft.VisualBasic.Logging.Log>   
 <xref:Microsoft.VisualBasic.ApplicationServices.User></xref:Microsoft.VisualBasic.ApplicationServices.User>   
 [どのように私はプロジェクトの種類に依存します](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)   
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)   
 [My.Forms オブジェクト](../../../visual-basic/language-reference/objects/my-forms-object.md)   
 [My.Request オブジェクト](../../../visual-basic/language-reference/objects/my-request-object.md)   
 [My.Response オブジェクト](../../../visual-basic/language-reference/objects/my-response-object.md)   
 [My.WebServices オブジェクト](../../../visual-basic/language-reference/objects/my-webservices-object.md)
