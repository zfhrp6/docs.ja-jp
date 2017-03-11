---
title: "/doc | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "doc compiler option [Visual Basic]"
  - "-doc compiler option [Visual Basic]"
  - "/doc compiler option [Visual Basic]"
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# /doc
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ドキュメント コメントを XML ファイルに出力します。  
  
## 構文  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`+`  &#124; `-`|省略可能です。  \+ を指定するか、または `/doc` だけを指定すると、コンパイラがドキュメント情報を生成し、XML ファイルに出します。  `-`  を指定すると、`/doc` を指定しないのと同じ意味になり、ドキュメント情報は作成されません。|  
|`file`|`/doc:` を使用する場合は、必ず指定します。  コンパイルするソース コード ファイルからコメントを書き込む、XML 形式の出力ファイルを指定します。  ファイル名に空白が含まれる場合は、二重引用符 \(" "\) で囲む必要があります。|  
  
## 解説  
 `/doc` オプションを使って、コンパイル時にドキュメント コメントを含む XML ファイルを生成するかどうかを制御できます。  `/doc:``file` の構文を使用する場合、`file` パラメーターには XML ファイルの名前を指定します。  `/doc` または `/doc+` を使用する場合、コンパイラは作成している実行可能ファイルまたはライブラリから XML ファイル名を取得します。  `/doc-` を使用するか、または `/doc` オプションを指定しなければ、コンパイラは XML ファイルを作成しません。  
  
 ソース コード ファイルでは、ドキュメント コメントは次の定義の前に記述できます。  
  
-   [クラス](../../../visual-basic/language-reference/statements/class-statement.md)や[インターフェイス](../../../visual-basic/language-reference/statements/interface-statement.md)などのユーザー定義型  
  
-   フィールド、[イベント](../../../visual-basic/language-reference/statements/event-statement.md)、[プロパティ](../../../visual-basic/language-reference/statements/property-statement.md)、[関数](../../../visual-basic/language-reference/statements/function-statement.md)、または[サブルーチン](../../../visual-basic/language-reference/statements/sub-statement.md)などのメンバー  
  
 生成した XML ファイルを [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] の [IntelliSense](/visual-studio/ide/using-intellisense) 機能で使用するには、XML ファイルの名前をサポートするアセンブリの名前と同じにします。  XML ファイルをアセンブリと同じディレクトリに格納して、アセンブリが [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] プロジェクトで参照されるとき、.xml ファイルも同時に見つかるようにしてください。  IntelliSense がプロジェクト内のコード、またはプロジェクトによって参照されるプロジェクト内のコードを処理するために、XML ドキュメント ファイルは必要ありません。  
  
 `/target:module` を使ってコンパイルしなければ、XML ファイルにはタグ `<assembly></assembly>` が記述されます。  これらのタグは、コンパイルによる出力ファイルのアセンブリ マニフェストを含むファイル名を指定します。  
  
 コード内のコメントからドキュメントを生成する方法については、「[XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)」を参照してください。  
  
||  
|-|  
|Visual Studio 統合開発環境で \/doc を設定するには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[コンパイル\]** タブをクリックします。<br />3.  **\[XML ドキュメント ファイルを生成する\]** ボックスに値を設定します。|  
  
## 使用例  
 具体的な例については、「[Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)」を参照してください。  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)