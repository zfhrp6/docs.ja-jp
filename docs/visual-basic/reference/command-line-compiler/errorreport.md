---
title: "/errorreport |Microsoft ドキュメント"
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
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2ebe5646256926f68a1a900b91c25a1768505785
ms.lasthandoff: 03/13/2017

---
# <a name="errorreport"></a>/errorreport
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラで内部コンパイル エラーを報告するかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a>コメント  
 このオプションは、レポートする便利な手段を提供、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を内部コンパイラ エラー (ICE)、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]マイクロソフトのチーム。 既定では、コンパイラによっていないマイクロソフトに情報。 ただし、内部コンパイラ エラーが発生した場合は、このオプション使用するエラーを Microsoft に報告できます。 その情報がマイクロソフトのエンジニアが原因の特定に役立つし、の次回のリリースを向上させるための[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]です。  
  
 レポートを送信するユーザーの機能は、コンピューターとユーザー ポリシーのアクセス許可によって異なります。  
  
 次の表に、影響、`/errorreport`オプション。  
  
|オプション|動作|  
|---|---|  
|`prompt`|内部コンパイラ エラーが発生した場合、ダイアログ ボックスが、コンパイラが収集された正確なデータを表示できるようにします。 エラー報告の機密情報があるかを判断し、マイクロソフトに送信するかどうかを判断することできます。 送信することを決定する、コンピューターおよびユーザー ポリシー設定で許可する場合、コンパイラは、データを Microsoft に送信します。|  
|`queue`|エラー レポート キューに入れます。 前回のログに記録されたエラーを報告するには管理者権限でログインするときに (いない適宜&3; 日間に複数回エラー レポートを送信する)。 これは、既定の動作と、`/errorreport`オプションが指定されていません。|  
|`send`|内部コンパイラ エラーが発生したコンピューターおよびユーザー ポリシー設定で許可する場合は、コンパイラは、データを Microsoft に送信します。<br /><br /> オプション`/errorReport:send`自動的にエラー情報をマイクロソフトに送信しようとしています。 このオプションは、レジストリに依存します。 レジストリで適切な値を設定する方法の詳細については、次を参照してください。[を Visual Studio 2008 コマンド ライン ツールでの自動エラー報告を有効にする方法](http://go.microsoft.com/fwlink/?LinkID=184695)します。|  
|`none`|内部コンパイラ エラーが発生した場合、収集またはされませんがマイクロソフトに送信します。|  
  
 コンパイラは、ソース コードは、通常は、エラー発生時にスタックを含むデータを送信します。 場合`/errorreport`と共に使用される、 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプション、ソース ファイル全体が送信されます。  
  
 このオプションはで最も多く使用、 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプション、マイクロソフトのエンジニアをより簡単にエラーを再現できるためです。  
  
> [!NOTE]
>  `/errorreport`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。  
  
## <a name="example"></a>例  
 次のコードをコンパイルしようとしました。 `T2.vb`、コンパイラには、内部コンパイラ エラーが発生すると、エラー レポートを Microsoft に送信することが確認されます。  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
