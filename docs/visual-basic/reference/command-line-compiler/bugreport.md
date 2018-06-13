---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 0383a5e369ee4a8146764c13b2f12f48ebe52190
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653495"
---
# <a name="-bugreport"></a>-bugreport
バグのレポートをファイルするときに使用できるファイルを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`file`|必須。 バグのレポートを格納するファイルの名前。 ファイル名を引用符で囲みます ("")、名前にスペースが含まれている場合。|  
  
## <a name="remarks"></a>コメント  
 次の情報に追加されます`file`:  
  
-   コンパイルですべてのソース コード ファイルのコピー。  
  
-   コンパイルで使用するコンパイラ オプションの一覧。  
  
-   コンパイラ、共通言語ランタイム、およびオペレーティング システムのバージョン情報。  
  
-   コンパイラの出力 (指定されている場合)。  
  
-   対象のされたら、問題の説明です。  
  
-   問題を検討する方法の説明は修正する必要があります、するように求められます。  
  
 すべてのソース コード ファイルのコピーが含まれているため`file`、できるだけ小さなプログラムに思われるコードの障害を再現することがあります。  
  
> [!IMPORTANT]
>  `-bugreport`オプションは、機密性の高い情報を含むファイルを生成します。 これにより、現在の時刻、コンパイラのバージョンが含まれます。[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]バージョン、オペレーティング システムのバージョン、ユーザー名、コマンドライン引数を、コンパイラが実行された、すべてのソース コードでは、参照されるアセンブリのいずれかのバイナリ形式です。 このオプションは、Web.config ファイルのサーバー側のコンパイルでのコマンド ライン オプションを指定することによってアクセスできる、[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]アプリケーションです。 これを回避するには、ユーザーがサーバーでのコンパイルが行われないよう、Machine.config ファイルを変更します。  
  
 このオプションを使用する場合`-errorreport:prompt`、 `-errorreport:queue`、または`-errorreport:send`、アプリケーションでの情報は、内部コンパイラ エラーが発生して`file`がマイクロソフトに送信します。 その情報はマイクロソフトのエンジニアが、エラーの原因を特定し、Visual Basic の次回リリースの改善に役立てます。 既定では、Microsoft に情報は送信されません。 ただしを使用してアプリケーションをコンパイルするときに`-errorreport:queue`、既定で有効にする、アプリケーションがエラー レポートを収集します。 次に、コンピューターの管理者がログインすると、エラー レポート システムにより、管理者は、ログオン以降に発生したすべてのエラー レポートを Microsoft に転送するポップアップ ウィンドウが表示されます。  
  
> [!NOTE]
>  `/bugreport`オプションは、Visual Studio 開発環境からは利用できません。 使用可能なコマンドラインからコンパイルするときにのみです。  
  
## <a name="example"></a>例  
 次の例をコンパイル`T2.vb`ファイルにバグ レポートのすべての情報を格納`Problem.txt`です。  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [デバッグ (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [-errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [securityPolicy (ASP.NET 設定スキーマ) の trustLevel 要素](http://msdn.microsoft.com/library/729ab04c-03da-4ee5-86b1-be9d08a09369)
