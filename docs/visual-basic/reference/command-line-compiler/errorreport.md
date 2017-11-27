---
title: /errorreport
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0abe276aaacdeb175c3af7067dffa81448450e22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="errorreport"></a>/errorreport
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラで内部コンパイル エラーを報告するかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>コメント  
 このオプションでは、レポートする便利な手段、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]を内部コンパイラ エラー (ICE)、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Microsoft のチームのです。 既定では、コンパイラ情報を送信しませんを Microsoft にします。 ただし、内部コンパイラ エラーが発生した場合は、このオプションにより、エラーを Microsoft に報告します。 その情報がマイクロソフトのエンジニアが原因の特定に役立つし、次のリリースの改善に役立つ[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。  
  
 レポートを送信するユーザーの機能は、コンピューターとユーザーのポリシー アクセス許可によって異なります。  
  
 次の表の影響、`/errorreport`オプション。  
  
|オプション|動作|  
|---|---|  
|`prompt`|内部コンパイラ エラーが発生する場合、ダイアログ ボックスが表示されたら、コンパイラが収集される正確なデータを表示できるようにします。 エラー報告の機密情報がある場合を判断し、Microsoft に送信するかどうかを判断することできます。 送信することを決定する、コンピューターとユーザー ポリシーの設定で許可する場合は、コンパイラは、データを Microsoft に送信します。|  
|`queue`|エラー レポートを待ち行列に入れます。 前回のログに記録されたエラーを報告するには管理者特権使用してログインするときに (いない求められます 3 日間に 2 回以上のエラー レポートを送信する)。 これは、既定の動作時に、`/errorreport`オプションが指定されていません。|  
|`send`|内部コンパイラ エラーが発生するコンピューターとユーザー ポリシーの設定で許可する場合は、コンパイラは、データを Microsoft に送信します。<br /><br /> オプション`/errorReport:send`エラー情報をマイクロソフトに自動的に送信しようとしています。 このオプションは、レジストリに依存します。 レジストリで、適切な値を設定する方法の詳細については、次を参照してください。[を Visual Studio 2008 コマンド ライン ツールで自動エラー報告を有効にする方法](http://go.microsoft.com/fwlink/?LinkID=184695)です。|  
|`none`|内部コンパイラ エラーが発生する場合、収集またはされませんがマイクロソフトに送信します。|  
  
 コンパイラは、通常いくつかのソース コードを含む、エラー発生時にスタックを含むデータを送信します。 場合`/errorreport`と共に使用される、 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプション、ソース ファイル全体が送信されます。  
  
 このオプションを使用して最適な[/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプション、マイクロソフトのエンジニアをより簡単にエラーを再現できるためです。  
  
> [!NOTE]
>  `/errorreport`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードをコンパイルしようとしました。 `T2.vb`、コンパイラには、内部コンパイラ エラーが発生すると、エラー レポートを Microsoft に送信することが確認されます。  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
