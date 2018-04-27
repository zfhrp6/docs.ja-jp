---
title: -errorreport
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dc321f7f927d68a9f270076640cbc6d31d2f6d5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="-errorreport"></a>-errorreport
Visual Basic コンパイラで内部コンパイラ エラーを報告する方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>コメント  
 このオプションは、microsoft Visual Basic チームに Visual Basic 内部コンパイル エラー (ICE) を報告する便利な手段を提供します。 既定では、コンパイラ情報を送信しませんを Microsoft にします。 ただし、内部コンパイラ エラーが発生した場合は、このオプションにより、エラーを Microsoft に報告します。 情報は、マイクロソフトのエンジニアが原因の特定に役立つし、次のリリースの Visual Basic の改善に役立てます。  
  
 レポートを送信するユーザーの機能は、コンピューターとユーザーのポリシー アクセス許可によって異なります。  
  
 次の表の影響、`-errorreport`オプション。  
  
|オプション|動作|  
|---|---|  
|`prompt`|内部コンパイラ エラーが発生する場合、ダイアログ ボックスが表示されたら、コンパイラが収集される正確なデータを表示できるようにします。 エラー報告の機密情報がある場合を判断し、Microsoft に送信するかどうかを判断することできます。 送信することを決定する、コンピューターとユーザー ポリシーの設定で許可する場合は、コンパイラは、データを Microsoft に送信します。|  
|`queue`|エラー レポートを待ち行列に入れます。 前回のログに記録されたエラーを報告するには管理者特権使用してログインするときに (いない求められます 3 日間に 2 回以上のエラー レポートを送信する)。 これは、既定の動作時に、`-errorreport`オプションが指定されていません。|  
|`send`|内部コンパイラ エラーが発生するコンピューターとユーザー ポリシーの設定で許可する場合は、コンパイラは、データを Microsoft に送信します。<br /><br /> オプション`-errorreport:send`エラー情報をマイクロソフトに自動的に送信しようとしています。 このオプションは、レジストリに依存します。 レジストリで、適切な値を設定する方法の詳細については、次を参照してください。[を Visual Studio 2008 コマンド ライン ツールで自動エラー報告を有効にする方法](http://go.microsoft.com/fwlink/?LinkID=184695)です。|  
|`none`|内部コンパイラ エラーが発生する場合、収集またはされませんがマイクロソフトに送信します。|  
  
 コンパイラは、通常いくつかのソース コードを含む、エラー発生時にスタックを含むデータを送信します。 場合`-errorreport`と共に使用される、 [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプション、ソース ファイル全体が送信されます。  
  
 このオプションを使用して最適な[/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプション、マイクロソフトのエンジニアをより簡単にエラーを再現できるためです。  
  
> [!NOTE]
>  `-errorreport`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードをコンパイルしようとしました。 `T2.vb`、コンパイラには、内部コンパイラ エラーが発生すると、エラー レポートを Microsoft に送信することが確認されます。  
  
```  
vbc -errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
