---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d28d0556a662099e4e5e74b22583fc3c8b4c313f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-vbruntime"></a>-vbruntime
コンパイラが Visual Basic Runtime Library を参照せずにコンパイルするか、特定のランタイム ライブラリを参照してコンパイルするかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a>引数  
 \-  
 Visual Basic ランタイム ライブラリへの参照なしでコンパイルします。  
  
 \+  
 既定の Visual Basic ランタイム ライブラリへの参照を使用してコンパイルします。  
  
 \*  
 Visual Basic ランタイム ライブラリへの参照なしでコンパイルして、コア機能を Visual Basic ランタイム ライブラリからアセンブリに埋め込みます。  
  
 `path`  
 指定したライブラリ (DLL) への参照を使用してコンパイルします。  
  
## <a name="remarks"></a>コメント  
 `-vbruntime`コンパイラ オプションでは、コンパイラがコンパイルを Visual Basic ランタイム ライブラリへの参照がないことを指定することができます。 Visual Basic ランタイム ライブラリへの参照がないことをコンパイルする場合は、エラーまたは警告が Visual Basic ランタイム ヘルパーへの呼び出しを生成するコードや言語の構造に記録されます。 (A *Visual Basic ランタイム ヘルパー*特定言語のセマンティックを実行する実行時に呼び出される Microsoft.VisualBasic.dll で定義されている関数です)。  
  
 `-vbruntime+`オプションがない場合に発生するのと同じ動作を生成する`-vbruntime`スイッチを指定します。 使用することができます、`-vbruntime+`以前オーバーライド オプションを指定`-vbruntime`スイッチ。  
  
 ほとんどのオブジェクト、`My`型は、使用する場合は使用できません、`-vbruntime-`または`-vbruntime:path`オプション。  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a>Visual Basic ランタイム コア機能の埋め込み  
 `-vbruntime*`オプションでは、ランタイム ライブラリへの参照なしでコンパイルすることができます。 代わりに、Visual Basic ランタイム ライブラリのコア機能は、ユーザー アセンブリに埋め込まれます。 Visual Basic ランタイムが含まれていないプラットフォームで、アプリケーションが実行する場合は、このオプションを使用することができます。  
  
 次のランタイムのメンバーが埋め込まれます。  
  
-   <xref:Microsoft.VisualBasic.CompilerServices.Conversions> クラス  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> メソッド  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> メソッド  
  
-   <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> メソッド  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> 定数  
  
-   一部のオブジェクトの`My`型  
  
 使用してコンパイルする場合、`-vbruntime*`オプションと、コードは、コア機能に埋め込まれていない、Visual Basic ランタイム ライブラリからメンバーを参照、コンパイラはメンバーが使用できないことを示すエラーを返します。  
  
## <a name="referencing-a-specified-library"></a>指定したライブラリを参照します。  
 使用することができます、`path`既定の Visual Basic ランタイム ライブラリではなく、カスタム ランタイム ライブラリへの参照を使用してコンパイルする引数。  
  
 場合の値、`path`引数が、DLL への完全修飾パスでは、コンパイラは、ランタイム ライブラリとそのファイルを使用します。 場合の値、`path`引数は、DLL への完全修飾パスではありません、Visual Basic コンパイラは最初に、現在のフォルダーで識別された DLL を検索します。 使用して、指定したパスの検索、 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)コンパイラ オプション。 場合、`-sdkpath`コンパイラ オプションを使用しない、コンパイラは、.NET Framework フォルダーで識別された DLL の検索 (`%systemroot%\Microsoft.NET\Framework\versionNumber`)。  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`-vbruntime`カスタム ライブラリへの参照を使用してコンパイルするにはオプションです。  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic コア – Visual Studio 2010 SP1 で新規のコンパイル モード](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
