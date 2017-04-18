---
title: "/warnaserror (Visual Basic) |Microsoft ドキュメント"
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
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: 18
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
ms.openlocfilehash: 28f232b1ad8200455550f2f4c1204818c8b143ab
ms.lasthandoff: 03/13/2017

---
# <a name="warnaserror-visual-basic"></a>/warnaserror (Visual Basic)
コンパイラで最初に発生した警告をエラーとして処理します。  
  
## <a name="syntax"></a>構文  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|+ &#124; -|省略可能です。 既定では、`/warnaserror-`が有効にします。 警告があって、コンパイラから出力ファイルを作成します。 `/warnaserror`は同じオプションとして`/warnaserror+`、警告をエラーとして扱うことです。|  
|`numberList`|省略可能です。 警告 ID のコンマ区切りの一覧の番号を`/warnaserror`オプションは適用されます。 警告 ID が指定されていない場合、`/warnaserror`オプションのすべての警告に適用されます。|  
  
## <a name="remarks"></a>コメント  
 `/warnaserror`オプションは、すべての警告をエラーとして扱います。 警告をエラーとしてレポートされる代わりに、通常は報告されるメッセージ。 コンパイラは警告として同じ警告のそれ以降の出現箇所を報告します。  
  
 既定では、`/warnaserror-`がこれにより、警告、情報提供だけに有効になっています。 `/warnaserror`は同じオプションとして`/warnaserror+`、警告をエラーとして扱うことです。  
  
 いくつかの特定の警告のみを実行する場合に、エラーとして扱う警告の番号をコンマで区切って指定できます。  
  
> [!NOTE]
>  `/warnaserror`オプションでは、警告を表示する方法は制御しません。 使用して、 [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)警告を無効にすることです。  
  
|Visual Studio IDE でのエラーとしてすべての警告を処理する/warnaserror を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.**[コンパイル]** タブをクリックします。<br />3.確認、**すべての警告を無効にする** チェック ボックスがオフになっています。<br />4.チェック、**すべての警告をエラーとして扱う**チェック ボックスをオンします。|  
  
|Visual Studio IDE でのエラーとして特定の警告を処理する/warnaserror を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。<br />2.**[コンパイル]** タブをクリックします。<br />3.確認、**すべての警告を無効にする** チェック ボックスがオフになっています。<br />4.確認、**すべての警告をエラーとして扱う** チェック ボックスがオフになっています。<br />5.選択**エラー**から、**通知**をエラーとして扱う警告の横にある列です。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`し、最初に見つかった位置が見つかったすべての警告をエラーとして表示することをコンパイラに指示します。  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`し、単に使用されていないローカル変数 (42024) の警告をエラーとして扱われます。  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)
