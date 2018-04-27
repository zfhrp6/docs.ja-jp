---
title: -netcf
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f07fc7988c4329397e464f05d334648e98cb129d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="-netcf"></a>-netcf
[!INCLUDE[Compact](~/includes/compact-md.md)] が対象になるようにコンパイラを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
-netcf  
```  
  
## <a name="remarks"></a>コメント  
 `-netcf`オプションは、ターゲットに Visual Basic コンパイラ、[!INCLUDE[Compact](~/includes/compact-md.md)]完全ではなく[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]です。 言語機能は完全にのみ存在する[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]は無効になります。  
  
 `-netcf`オプションで使用するように設計された[-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)です。 無効になっている言語機能`-netcf`、同じ言語機能を対象となるファイル内に存在しない`-sdkpath`です。  
  
> [!NOTE]
>  `-netcf`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。 `-netcf` Visual Basic プロジェクトのデバイスが読み込まれるときに、オプションを設定します。  
  
 `-netcf`オプションは次の言語機能を変更します。  
  
-   [終了\<キーワード > ステートメント](../../../visual-basic/language-reference/statements/end-keyword-statement.md)プログラムの実行を終了するには、キーワードが無効になっています。 次のプログラムをコンパイルしてなしで実行されます`-netcf`はコンパイル時に失敗した`-netcf`です。  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   遅延バインディングするには、すべての形式が無効です。 認識された遅延バインディングのシナリオが発生した場合に、コンパイル時エラーが生成されます。 次のプログラムをコンパイルしてなしで実行されます`-netcf`はコンパイル時に失敗した`-netcf`です。  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   [自動](../../../visual-basic/language-reference/modifiers/auto.md)、 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)、および[Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)修飾子が無効になっています。 構文、 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)ステートメントが変更にも`Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`します。 次のコードは、の効果を示しています。 `-netcf` 、コンパイル時にします。  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   Visual Basic から削除された Visual Basic 6.0 のキーワードを使用して、別のエラーが生成されるとき`-netcf`を使用します。 これには、次のキーワードのエラー メッセージに影響します。  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## <a name="example"></a>例  
 次のコードのコンパイル`Myfile.vb`で、[!INCLUDE[Compact](~/includes/compact-md.md)]の既定のインストール ディレクトリで見つかった mscorlib.dll および Microsoft.VisualBasic.dll のバージョンを使用して、[!INCLUDE[Compact](~/includes/compact-md.md)]が C ドライブにします。 通常の最新バージョンを使用すると、[!INCLUDE[Compact](~/includes/compact-md.md)]です。  
  
```console  
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)
