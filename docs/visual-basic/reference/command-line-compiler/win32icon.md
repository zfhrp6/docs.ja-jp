---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 045e621f0104c4c958d77d2443c1524b33410b7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-win32icon"></a>-win32icon
.Ico ファイルを出力ファイルに挿入します。 この .ico ファイルは出力ファイルを表す**ファイル エクスプ ローラー**です。  
  
## <a name="syntax"></a>構文  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`filename`|出力ファイルに追加する .ico ファイル。 ファイル名を引用符で囲みます ("")、スペースが含まれている場合。|  
  
## <a name="remarks"></a>コメント  
 .Ico ファイルは、Microsoft Windows リソース コンパイラ (RC) を作成できます。 リソース コンパイラが、Visual C プログラムをコンパイルするときに呼び出されます.ico ファイルは .rc ファイルから作成されます。 `-win32icon`と`-win32resource`オプションは相互に排他的です。  
  
 参照してください[-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)参照に、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]リソース ファイル、または[-リソース (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)をアタッチする、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]リソース ファイル。 参照してください[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res ファイルをインポートします。  
  
|Visual Studio IDE で win32icon を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[アプリケーション]** タブをクリックします。<br />3.値を変更、**アイコン**ボックス。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`.ico ファイルをアタッチおよび`Rf.ico`です。  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
