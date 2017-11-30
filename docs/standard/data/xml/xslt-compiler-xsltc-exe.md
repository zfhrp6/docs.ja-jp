---
title: "XSLT コンパイラ (xsltc.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2b4ede7bdb8dad65e9cd959dfaa2f8956a877762
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-compiler-xsltcexe"></a>XSLT コンパイラ (xsltc.exe)
XSLT コンパイラ (xsltc.exe) は、XSLT スタイル シートをコンパイルしてアセンブリを生成します。 コンパイルしたスタイル シートを <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> メソッドに直接渡すことができます。 xsltc.exe を使用して署名があるアセンブリを生成することはできません。  
  
 xsltc.exe ツールは Visual Studio 2008 に付属しています。 詳細については、次を参照してください。、 [Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/?LinkId=89463)です。  
  
## <a name="syntax"></a>構文  
  
```  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a>引数  
  
|引数|説明|  
|--------------|-----------------|  
|`sourceFile`|スタイル シートの名前を指定します。 スタイル シートはローカル ファイルであるか、イントラネット上に置かれていることが必要です。|  
  
## <a name="options"></a>オプション  
  
|オプション|説明|  
|------------|-----------------|  
|`/c[lass]:` `name`|以降のスタイル シートのクラス名を指定します。 クラス名には完全修飾名を指定できます。<br /><br /> 既定のクラス名は、スタイル シートの名前です。 たとえば、スタイル シート customers.xsl をコンパイルした場合、既定のクラス名は customers になります。|  
|`/debug[`+&#124;-`]`|デバッグ情報を生成するかどうかを指定します。<br /><br /> `+` または `/debug` を指定すると、コンパイラによりデバッグ情報が生成され、プログラム データベース (PDB) ファイルに記録されます。 生成される PDB ファイルの名前は `assemblyName`.pdb です。<br /><br /> `-` を指定しない場合、`/debug` の指定が有効となります。これを指定した場合、デバッグ情報は作成されません。 製品版のアセンブリが生成されます。 **注:**デバッグ モードでコンパイルでは、XSLT のパフォーマンスを大幅に影響します。|  
|`/help`|このツールのコマンド構文とオプションを表示します。|  
|`/nologo`|コンパイラの著作権メッセージが表示されないようにします。|  
|`/platform:` `string`|アセンブリを実行できるプラットフォームを指定します。 次に、有効なプラットフォームの値を示します。<br /><br /> `x86` : 32 ビット x86 互換共通言語ランタイムにより実行できるように、アセンブリをコンパイルします。<br /><br /> `x64` : AMD64 または EM64T 命令セットをサポートするコンピューターで 64 ビット共通言語ランタイムにより実行できるように、アセンブリをコンパイルします<br /><br /> [!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)]インストールされているコンピューターで 64 ビット共通言語ランタイムで実行するアセンブリをコンパイル、[!INCLUDE[vcpritanium](../../../../includes/vcpritanium-md.md)]プロセッサ。<br /><br /> `anycpu` : 任意のプラットフォーム上で実行できるように、アセンブリをコンパイルします。 既定値です。|  
|`/out:` `assemblyName`|出力となるアセンブリの名前を指定します。 複数のスタイル シートが存在している場合、既定のアセンブリ名はメインのスタイル シートか最初のスタイル シートの名前になります。<br /><br /> スタイル シートにスクリプトが含まれている場合、スクリプトは別のアセンブリに保存されます。 スクリプト アセンブリ名は、メインのアセンブリ名から生成されます。 たとえば、アセンブリ名を CustOrders.dll と指定した場合、最初のスクリプト アセンブリは CustOrders_Script1.dll という名前になります。|  
|`/settings:` `document+-, script+-, DTD+-,`|スタイル シートで `document()` 関数、XSLT スクリプト、またはドキュメント型定義 (DTD) を許可するかどうかを指定します。<br /><br /> 既定では、DTD、`document()` 関数、スクリプトのサポートは無効になっています。|  
|`@` `file`|コンパイラ オプションを含むファイルを指定できます。|  
|`?`|このツールのコマンド構文とオプションを表示します。|  
  
## <a name="remarks"></a>コメント  
 XSLT ソリューションは、複数のスタイル シート モジュールで構成できます。 xsltc.exe ツールを使用して、スタイル シートからアセンブリを生成できます。 このアセンブリを <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> メソッドに直接渡すことができます。 XSLT の配置シナリオによっては、これによってパフォーマンス コストを削減できます。  
  
> [!NOTE]
>  アプリケーションには、コンパイル済みのアセンブリも参照として含める必要があります。  
  
 Xsltc.exe ツールは、クラスを検証できません (`/class:``name`) またはアセンブリ (`/out:``assemblyName`) の名前。 名前が無効である場合、共通言語ランタイムによってエラーがスローされます。  
  
## <a name="examples"></a>例  
 次のコマンドを実行すると、スタイル シートがコンパイルされ、booksort.dll という名前のアセンブリが作成されます。  
  
```  
xsltc booksort.xsl  
```  
  
 次のコマンドを実行すると、スタイル シートがコンパイルされ、booksort.dll という名前のアセンブリと booksort.pdb という名前の PDB ファイルが作成されます。  
  
```  
xsltc booksort.xsl /debug  
```  
  
 次のコマンドを実行すると、msxsl:script 要素を含むスタイル シートがコンパイルされ、calc.dll および calc_Script1.dll という 2 つのアセンブリが作成されます。  
  
```  
xsltc /settings:script+ calc.xsl  
```  
  
 次のコマンドを実行すると、DTD 処理とスタイルのサポートが有効になり、myTest.dll および myTest_Script1.dll という 2 つのアセンブリが作成されます。  
  
```  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 次のコマンドを実行すると、2 つのスタイル シート モジュールがコンパイルされ、booksort.dll という名前のアセンブリが 1 つ作成されます。  
  
```  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [方法: アセンブリを使用して XSLT 変換を実行](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)  
 [XSLT 変換](../../../../docs/standard/data/xml/xslt-transformations.md)
