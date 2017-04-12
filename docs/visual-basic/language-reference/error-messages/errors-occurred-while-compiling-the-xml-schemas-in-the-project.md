---
title: "プロジェクトでは、XML スキーマのコンパイル中にエラーが発生しました |。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
dev_langs:
- VB
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: 11
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
ms.openlocfilehash: cf04e85da98db53d1c78269169571936f708cd21
ms.lasthandoff: 03/13/2017

---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>プロジェクトで、XML スキーマのコンパイル中にエラーが発生しました
プロジェクトでは、XML スキーマのコンパイル中にエラーが発生しました。 このため、XML IntelliSense は使用できません。  
  
 プロジェクトに含まれる XML スキーマ定義 (XSD) スキーマでエラーがあります。 このエラーは、既存の XSD スキーマとの競合がプロジェクトに設定する XSD スキーマ (.xsd) ファイルを追加するときに発生します。  
  
 **エラー ID:** BC36810  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   警告をダブルクリック、**エラー リスト**ウィンドウです。 Visual Basic をクリックすると、警告の原因となった XSD ファイル内の場所。 XSD スキーマのエラーを修正します。  
  
-   必要なすべての XSD スキーマ (.xsd) ファイルがプロジェクトに含まれていることを確認します。 をクリックする必要があります**すべてのファイル**上、**プロジェクト**にファイルを .xsd を表示するメニュー**ソリューション エクスプ ローラー**します。 .Xsd ファイルを右クリックし、**プロジェクトに含める**プロジェクトにファイルを追加します。  
  
-   XML to Schema ウィザードを使用するいると、同じソースから&2; 回以上のスキーマを推論する場合にこのエラーが発生することができます。 この場合、既存の XSD スキーマ ファイルを削除するには、プロジェクトから新しい XML スキーマ項目テンプレートを追加とし、XML to Schema ウィザードに提供適用可能なすべての XML ソース プロジェクトにします。  
  
-   XSD スキーマでエラーが指定されていない場合、XML コンパイラは十分な情報、詳細なエラー メッセージを提供することはできません。 プロジェクト一致に含まれる .xsd ファイルの XML 名前空間が、Visual Studio で設定する XML スキーマで特定された XML 名前空間を使用することを確認する場合は、詳細なエラー情報を取得することができます。  
  
## <a name="see-also"></a>関連項目  
 [エラー一覧 ウィンドウ](https://docs.microsoft.com/visualstudio/ide/reference/error-list-window)   
 [Visual Basic における XML IntelliSense](../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
