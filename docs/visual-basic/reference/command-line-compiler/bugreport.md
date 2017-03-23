---
title: "/bugreport |Microsoft ドキュメント"
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
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: 22
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
ms.openlocfilehash: 9c64ec49d7e6842edbc0fed7407a34132a8f5a88
ms.lasthandoff: 03/13/2017

---
# <a name="bugreport"></a>/bugreport
バグのレポートをファイルするときに使用できるファイルを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
/bugreport:file  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`file`|必須です。 バグのレポートを格納するファイルの名前。 ファイル名を引用符で囲みます ("") 名前にスペースが含まれている場合。|  
  
## <a name="remarks"></a>コメント  
 次の情報が追加`file`:  
  
-   コンパイルですべてのソース コード ファイルのコピー。  
  
-   コンパイル時に使用するコンパイラ オプションの一覧。  
  
-   コンパイラ、共通言語ランタイム、およびオペレーティング システムのバージョン情報。  
  
-   コンパイラが存在する場合に出力します。  
  
-   対象が表示されたら、問題の説明です。  
  
-   表示されたらどの問題を考えるの説明を修正する必要があります。  
  
 すべてのソース コード ファイルのコピーが含まれているため`file`、できるだけ小さなプログラムに思われるコード障害を再現することもできます。  
  
> [!IMPORTANT]
>  `/bugreport`オプションには、重要な情報を含むファイルが生成されます。 これにより、現在の時刻、コンパイラのバージョンが含まれます。[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]バージョン、オペレーティング システムのバージョン、ユーザー名、コマンドライン引数をコンパイラが実行されて、すべてのソース コードと参照アセンブリのいずれかのバイナリ形式です。 このオプションは、Web.config ファイルのサーバー側のコンパイルでのコマンド ライン オプションを指定することでアクセスできる、[!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]アプリケーションです。 これを防ぐためには、ユーザーが、サーバーでのコンパイルが行われないよう、Machine.config ファイルを変更します。  
  
 このオプションを使用する場合`/errorreport:prompt`、 `/errorreport:queue`、または`/errorreport:send`、アプリケーションでの情報は、内部コンパイラ エラーが発生して`file`はマイクロソフトに送信します。 その情報がマイクロソフトのエンジニアが、エラーの原因の特定に役立つし、の次回のリリースを向上させるための[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]です。 既定では、マイクロソフトに情報は送信されません。 ただしを使用してアプリケーションをコンパイルするときに`/errorreport:queue`、既定で有効にする、アプリケーションがエラー レポートを収集します。 次に、コンピューターの管理者がログインすると、エラー レポート システム管理者がログオン以降に発生したすべてのエラー レポートをマイクロソフトに転送できるようにするポップアップ ウィンドウが表示されます。  
  
> [!NOTE]
>  `/bugreport`オプションは、Visual Studio 開発環境内から使用できません。 は、コマンドラインからコンパイルする場合のみです。  
  
## <a name="example"></a>例  
 次の例をコンパイル`T2.vb`ファイルにすべてのバグのレポートの情報を格納`Problem.txt`します。  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)   
 [/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [(ASP.NET 設定スキーマ) securityPolicy の trustLevel 要素](http://msdn.microsoft.com/en-us/729ab04c-03da-4ee5-86b1-be9d08a09369)
