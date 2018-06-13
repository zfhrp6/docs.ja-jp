---
title: -メイン
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51a527dfddd2b78ac1c0559420298a66eb4b63f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652923"
---
# <a name="-main"></a>-メイン
`Sub Main` プロシージャを格納するクラスまたはモジュールを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-main:location  
```  
  
## <a name="arguments"></a>引数  
 `location`  
 必須。 クラスまたはを含むモジュールの名前、`Sub Main`プログラムの開始時に呼び出されるプロシージャです。 これがフォームになっている可能性があります **-メイン: モジュール**または **-main:namespace.module**です。  
  
## <a name="remarks"></a>コメント  
 実行可能ファイルまたは Windows 実行可能プログラムを作成するときに、このオプションを使用します。 場合、 **-メイン**オプションを省略すると、コンパイラは、有効な共有検索`Sub Main`ですべてのパブリック クラスとモジュール。  
  
 参照してください[Visual Basic の Main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)については、さまざまな形式の`Main`プロシージャです。  
  
 ときに`location`から継承するクラスは、 <xref:System.Windows.Forms.Form>、コンパイラは、既定値を提供`Main`クラスにない場合は、アプリケーションを起動するプロシージャ`Main`プロシージャです。 これにより、開発環境で作成されたコマンド ラインでコードをコンパイルできます。  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Set - Visual Studio 統合開発環境で主に  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **[アプリケーション]** タブをクリックします。  
  
3.  確認してください、**有効にするアプリケーション フレームワーク** チェック ボックスをオフになっています。  
  
4.  値を変更、**スタートアップ オブジェクト**ボックス。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`と`T3.vb`を指定してを`Sub Main`プロシージャが含まれて、`Test2`クラスです。  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Visual Basic の main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
