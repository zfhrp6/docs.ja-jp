---
title: "/vbruntime |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbruntime
- /vbruntime
dev_langs:
- VB
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: 17
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
ms.openlocfilehash: 455f950988b540b74874ce38882c59059f77ea8f
ms.lasthandoff: 03/13/2017

---
# <a name="vbruntime"></a>/vbruntime
コンパイラが Visual Basic Runtime Library を参照せずにコンパイルするか、特定のランタイム ライブラリを参照してコンパイルするかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>引数  
 \-  
 Visual Basic ランタイム ライブラリへの参照なしでコンパイルします。  
  
 \+  
 既定の Visual Basic ランタイム ライブラリへの参照を使用してコンパイルします。  
  
 \*  
 Visual Basic ランタイム ライブラリへの参照なしでコンパイルされ、アセンブリに Visual Basic ランタイム ライブラリのコア機能を埋め込みます。  
  
 `path`  
 指定したライブラリ (DLL) への参照を使用してコンパイルします。  
  
## <a name="remarks"></a>コメント  
 `/vbruntime`コンパイラ オプションでは、コンパイラがコンパイルを Visual Basic ランタイム ライブラリへの参照がないことを指定することができます。 Visual Basic ランタイム ライブラリを参照しないでコンパイルする場合、Visual Basic ランタイム ヘルパー呼び出しを生成するコードや言語の構造にエラーまたは警告が記録されます。 (A *Visual Basic ランタイム ヘルパー*特定言語のセマンティックを実行する実行時に呼び出される Microsoft.VisualBasic.dll で定義されている関数です)。  
  
 `/vbruntime+`オプションを指定しない場合に発生するのと同じ動作を出力する`/vbruntime`スイッチを指定します。 使用することができます、`/vbruntime+`前オーバーライド オプションを指定`/vbruntime`スイッチです。  
  
 ほとんどのオブジェクト、`My`型は、使用する場合は使用できません、`/vbruntime-`または`vbruntime:``path`オプション。  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Visual Basic ランタイムのコア機能を埋め込む  
 `/vbruntime*`オプションでは、ランタイム ライブラリへの参照なしでコンパイルすることができます。 代わりに、Visual Basic ランタイム ライブラリのコア機能は、ユーザー アセンブリに埋め込まれます。 Visual Basic ランタイムが含まれていないプラットフォームで、アプリケーションが実行されている場合は、このオプションを使用することができます。  
  
 次のランタイムのメンバーが埋め込まれます。  
  
-   <xref:Microsoft.VisualBasic.CompilerServices.Conversions>クラス</xref:Microsoft.VisualBasic.CompilerServices.Conversions>  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>メソッド</xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29>  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>メソッド</xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29>  
  
-   <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>メソッド</xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack>定数</xref:Microsoft.VisualBasic.Constants.vbBack>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr>定数</xref:Microsoft.VisualBasic.Constants.vbCr>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf>定数</xref:Microsoft.VisualBasic.Constants.vbCrLf>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed>定数</xref:Microsoft.VisualBasic.Constants.vbFormFeed>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf>定数</xref:Microsoft.VisualBasic.Constants.vbLf>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine>定数</xref:Microsoft.VisualBasic.Constants.vbNewLine>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar>定数</xref:Microsoft.VisualBasic.Constants.vbNullChar>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString>定数</xref:Microsoft.VisualBasic.Constants.vbNullString>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab>定数</xref:Microsoft.VisualBasic.Constants.vbTab>  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab>定数</xref:Microsoft.VisualBasic.Constants.vbVerticalTab>  
  
-   一部のオブジェクトの`My`型  
  
 使用してコンパイルした場合、`/vbruntime*`オプションと、コードは、コア機能に埋め込まれていない Visual Basic ランタイム ライブラリのメンバーを参照、コンパイラはメンバーが使用できないことを示すエラーを返します。  
  
## <a name="referencing-a-specified-library"></a>指定したライブラリを参照します。  
 使用することができます、 `path` Visual Basic ランタイム ライブラリの既定ではなくカスタムのランタイム ライブラリへの参照をコンパイルする引数。  
  
 場合の値、`path`引数が、DLL への完全修飾パスでは、コンパイラは、ランタイム ライブラリとそのファイルを使用します。 場合の値、`path`引数が、DLL への完全修飾パスではない、Visual Basic コンパイラは、現在のフォルダーで識別された DLL の最初に検索します。 使用して、指定したパスの検索、 [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)コンパイラ オプション。 場合、`/sdkpath`コンパイラ オプションは使用しない場合、コンパイラは、特定の DLL を .NET Framework フォルダーに検索されます (`%systemroot%\Microsoft.NET\Framework\versionNumber`)。  
  
## <a name="example"></a>例  
 次の例では、使用する方法、`/vbruntime`カスタム ライブラリへの参照を使用してコンパイルするにはオプションです。  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic コア – Visual Studio 2010 SP1 での新しいコンパイル モード](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)   
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
