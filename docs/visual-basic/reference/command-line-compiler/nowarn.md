---
title: /nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8da27ea2f9f0a4d370928d70cda1a796b822d97c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nowarn"></a>/nowarn
警告を生成するコンパイラの機能を無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`numberList`|省略可能です。 コンパイラはしないようにする警告の ID 番号のコンマ区切り一覧。 警告の Id が指定されていない場合、すべての警告は抑制されます。|  
  
## <a name="remarks"></a>コメント  
 `/nowarn`オプションにより、コンパイラの警告を生成しないことができます。 個々 の警告を抑制するのに警告の ID を指定、`/nowarn`コロンの後ろのオプションです。 複数の警告番号をカンマで区切ります。  
  
 警告 id の数値の一部だけを指定する必要があります。 たとえば、BC42024、未使用のローカル変数に対する警告を抑制する場合を指定`/nowarn:42024`です。  
  
 警告 ID 番号の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。  
  
|開発環境を統合するには、Visual Studio での/nowarn の設定|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.**[コンパイル]** タブをクリックします。<br />3.選択、**すべての警告を無効にする**すべての警告を無効にする チェック ボックスです。<br />     または<br />     特定の警告を無効にするには、 **None**警告の横にあるドロップダウン リストからです。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`し、すべての警告を表示しません。  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`し、使用されていないローカル変数 (42024) に警告を表示しません。  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)
