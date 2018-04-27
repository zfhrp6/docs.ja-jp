---
title: -ドキュメント
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7dc75a0600c9694c4a20f028c810c6aca54eeb6
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="-doc"></a>-ドキュメント
ドキュメント コメントを XML ファイルに出力します。  
  
## <a name="syntax"></a>構文  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`+` &#124; `-`|任意。 指定する +、または単`-doc`、コンパイラでドキュメント情報を生成し、XML ファイル内に配置します。 指定する`-`を指定しないことに相当`-doc`、なり、ドキュメントの情報を作成します。|  
|`file`|`-doc:` を使用する場合に、必ず指定します。 コンパイルのソース コード ファイルからのコメントが設定されている出力 XML ファイルを指定します。 ファイル名にスペースが含まれている場合は、引用符で囲まれます名を囲む ("") です。|  
  
## <a name="remarks"></a>コメント  
 `-doc`オプションでは、コンパイラがドキュメント コメントを含む XML ファイルを生成するかどうかを制御します。 使用する場合、`-doc:file`構文、`file`パラメーターは、XML ファイルの名前を指定します。 使用する場合`-doc`または`-doc+`コンパイラは、実行可能ファイルまたはコンパイラを作成しているライブラリから XML ファイルの名前を取得します。 使用する場合`-doc-`かを指定しない、`-doc`オプション、コンパイラは XML ファイルを作成しません。  
  
 ソース コード ファイル、ドキュメントのコメントは、次の定義前に記述できます。  
  
-   ユーザー定義型など、[クラス](../../../visual-basic/language-reference/statements/class-statement.md)または[インターフェイス](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   メンバーのフィールドなど、[イベント](../../../visual-basic/language-reference/statements/event-statement.md)、[プロパティ](../../../visual-basic/language-reference/statements/property-statement.md)、[関数](../../../visual-basic/language-reference/statements/function-statement.md)、または[サブルーチン](../../../visual-basic/language-reference/statements/sub-statement.md)です。  
  
 Visual Studio で生成された XML ファイルを使用する[IntelliSense](/visualstudio/ide/using-intellisense)機能をサポートするアセンブリと同じである XML ファイルのファイル名を使用します。 XML ファイルが、アセンブリと同じディレクトリにアセンブリが、Visual Studio プロジェクトで参照されている場合、.xml ファイルが見つかるも確認してください。 XML ドキュメント ファイルは IntelliSense コード プロジェクトによって参照されるプロジェクトまたはプロジェクト内で作業するために必要ではありません。  
  
 コンパイルする場合を除き、 `/target:module`、XML ファイルには、タグが含まれています。`<assembly></assembly>`です。 これらのタグは、コンパイルの出力ファイルのアセンブリ マニフェストを含むファイルの名前を指定します。  
  
 参照してください[XML コメント タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)コードのコメントからドキュメントを生成する方法についてです。  
  
|Visual Studio でのドキュメントが開発環境を統合するには set-|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[コンパイル]** タブをクリックします。<br />3.値を設定、**生成の XML ドキュメント ファイル**ボックス。|  
  
## <a name="example"></a>例  
 参照してください[XML でコードを文書化](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)サンプルについてはします。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [XML の使用によるコードのドキュメントの作成](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
