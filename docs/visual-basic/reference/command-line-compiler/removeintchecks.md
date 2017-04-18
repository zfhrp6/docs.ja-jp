---
title: "/removeintchecks |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
dev_langs:
- VB
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: 14
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
ms.openlocfilehash: 8e50200b8755ccc6b1c173024856955f5075b67e
ms.lasthandoff: 03/13/2017

---
# <a name="removeintchecks"></a>/removeintchecks
オーバーフロー エラーのオン/オフ、整数演算のチェックをオンにします。  
  
## <a name="syntax"></a>構文  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`+` &#124; `-`|省略可能です。 `/removeintchecks-`オプションによって、コンパイラは、すべての整数の計算でオーバーフロー エラーを確認します。 既定値は、`/removeintchecks-` です。<br /><br /> 指定する`/removeintchecks`または`/removeintchecks+`により、エラー チェックを行うと、高速の整数の計算を行うことができます。 エラーは、次のチェックを行わないただし、エラーを発生させずに不適切な結果が保存されるデータ型の容量がオーバーフローした場合とします。|  
  
|統合開発環境 Visual Studio で/removeintchecks を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.**[コンパイル]** タブをクリックします。<br />3.[詳細設定 **** ] ボタンをクリックします。<br />4.値を変更、**整数オーバーフローのチェックを解除**ボックス。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`Test.vb`し整数オーバーフロー エラー チェックをオフにします。  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
