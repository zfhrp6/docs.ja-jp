---
title: "/doc |Microsoft ドキュメント"
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
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
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
ms.openlocfilehash: 1054eb256eb7670ee0454b02fc094e0306c1218d
ms.lasthandoff: 03/13/2017

---
# <a name="doc"></a>/doc
ドキュメント コメントを XML ファイルに出力します。  
  
## <a name="syntax"></a>構文  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`+` &#124; `-`|省略可能です。 指定する +、または単`/doc`、コンパイラが、ドキュメントの情報が生成され、XML ファイルに配置します。 指定する`-`を指定しないと同じ`/doc`、なり、ドキュメント情報を作成します。|  
|`file`|`/doc:` を使用する場合に、必ず指定します。 コンパイルのソース コード ファイルからコメントが表示された出力 XML ファイルを指定します。 ファイル名にスペースが含まれている場合、名前を引用符で囲みます ("") です。|  
  
## <a name="remarks"></a>コメント  
 `/doc`オプションでは、コンパイラは、ドキュメント コメントを含む XML ファイルを生成するかどうかを制御します。 使用する場合、 `/doc:``file` 、構文、`file`パラメーターは、XML ファイルの名前を指定します。 使用する場合`/doc`または`/doc+`コンパイラは、実行可能ファイルまたはコンパイラを作成しているライブラリから、XML ファイル名を取得します。 使用する場合`/doc-`を指定しないか、`/doc`オプション、コンパイラは XML ファイルを作成しません。  
  
 ソース コード ファイルは、ドキュメントのコメントは、次の定義前に記述できます。  
  
-   ユーザー定義型など、[クラス](../../../visual-basic/language-reference/statements/class-statement.md)または[インターフェイス](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   フィールドなどのメンバー[イベント](../../../visual-basic/language-reference/statements/event-statement.md)、[プロパティ](../../../visual-basic/language-reference/statements/property-statement.md)、[関数](../../../visual-basic/language-reference/statements/function-statement.md)、または[サブルーチン](../../../visual-basic/language-reference/statements/sub-statement.md)します。  
  
 生成された XML ファイルを使用して、 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] [IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense)機能をサポートするアセンブリと同じである XML ファイルのファイル名を使用します。 XML ファイルが設定されて、アセンブリと同じディレクトリ内でアセンブリを参照するときになっていることを確認、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]プロジェクト、.xml ファイルがあるとします。 XML ドキュメント ファイルは、IntelliSense コード プロジェクトによって参照されるプロジェクトまたはプロジェクト内で動作するために必要ではありません。  
  
 コンパイルする場合を除き、 `/target:module`、XML ファイルには、タグが含まれています。`<assembly></assembly>`します。 これらのタグは、コンパイルの出力ファイルのアセンブリ マニフェストを含むファイルの名前を指定します。  
  
 参照してください[XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)コード内のコメントからドキュメントを生成する方法についてです。  
  
|統合開発環境 Visual Studio で/doc を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.**[コンパイル]** タブをクリックします。<br />3.値を設定、**生成 XML ドキュメント ファイル**ボックス。|  
  
## <a name="example"></a>例  
 参照してください[コードを XML で文書化](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)サンプルです。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [XML の使用によるコードのドキュメントの作成](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
