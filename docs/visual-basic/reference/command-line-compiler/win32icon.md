---
title: "/win32icon |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: 13
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
ms.openlocfilehash: 110a3861d6628dc2c3fb251aaa31762fb94f04c9
ms.lasthandoff: 03/13/2017

---
# <a name="win32icon"></a>/win32icon
.Ico ファイルは、出力ファイルに挿入します。 この .ico ファイルに出力ファイルを表す**ファイル エクスプ ローラー**します。  
  
## <a name="syntax"></a>構文  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`filename`|出力ファイルに追加する .ico ファイルです。 ファイル名を引用符で囲みます ("")、スペースが含まれている場合。|  
  
## <a name="remarks"></a>コメント  
 .Ico ファイルは、Microsoft Windows リソース コンパイラ (RC) を作成できます。 Visual C プログラムをコンパイルするときに、リソース コンパイラが呼び出されます.ico ファイルは .rc ファイルから作成されます。 `/win32icon`と`/win32resource`オプションは相互に排他的です。  
  
 参照してください[/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)参照に、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]リソース ファイルまたは[/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)をアタッチする、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]リソース ファイル。 参照してください[/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res ファイルをインポートします。  
  
|Visual Studio IDE で/win32icon を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.**[アプリケーション]** タブをクリックします。<br />3.値を変更、**アイコン**ボックス。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`.ico ファイルをアタッチおよび`Rf.ico`です。  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
