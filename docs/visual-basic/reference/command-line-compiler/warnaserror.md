---
title: /warnaserror (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d472795affe0df098d1551daf51a2f0ae20723ba
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
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
|+ &#124; -|任意。 既定では、`/warnaserror-`が有効になります。 警告は妨げませんコンパイラ出力ファイルを作成します。 `/warnaserror`オプションは、同じとして`/warnaserror+`、警告をエラーとして扱うことです。|  
|`numberList`|任意。 警告 ID のコンマ区切りの一覧の番号を`/warnaserror`オプションが適用されます。 警告 ID が指定されていない場合、`/warnaserror`オプションのすべての警告に適用されます。|  
  
## <a name="remarks"></a>コメント  
 `/warnaserror`オプションは、すべての警告をエラーとして扱います。 警告をエラーとしてレポートされる代わりに、通常は報告されるメッセージ。 コンパイラは警告として同じ警告のそれ以降の出現箇所を報告します。  
  
 既定では、`/warnaserror-`が有効で、情報提供だけを使用する警告の原因になっています。 `/warnaserror`オプションは、同じとして`/warnaserror+`、警告をエラーとして扱うことです。  
  
 いくつかの特定の警告のみを実行する場合に、エラーとして扱う警告番号のコンマ区切りの一覧を指定することがあります。  
  
> [!NOTE]
>  `/warnaserror`オプションでは、警告を表示する方法は制御しません。 使用して、 [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)警告を無効にするオプションです。  
  
|すべての警告、Visual Studio IDE でのエラーとして扱う/warnaserror を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[コンパイル]** タブをクリックします。<br />3.確認してください、**すべての警告を無効にする** チェック ボックスがオフになっています。<br />4.チェック、**すべての警告をエラーとして扱う**チェック ボックスをオンします。|  
  
|Visual Studio IDE でのエラーとして特定の警告を処理する/warnaserror を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。<br />2.**[コンパイル]** タブをクリックします。<br />3.確認してください、**すべての警告を無効にする** チェック ボックスがオフになっています。<br />4.確認、**すべての警告をエラーとして扱う** チェック ボックスがオフになっています。<br />5.選択**エラー**から、**通知**をエラーとして扱う警告の横にある列です。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`し、最初に見つかった位置が見つかったすべての警告をエラーとして表示することをコンパイラに指示します。  
  
```  
vbc /warnaserror in.vb  
```  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`エラーとして使用されていないローカル変数 (42024) に対する警告のみを処理します。  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>参照  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)
