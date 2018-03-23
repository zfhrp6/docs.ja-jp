---
title: -インポート (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d81e9d2bd55e6e38e337805b950a0b85680d129b
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-imports-visual-basic"></a>-インポート (Visual Basic)
指定したアセンブリから名前空間をインポートします。  
  
## <a name="syntax"></a>構文  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`namespaceList`|必須。 インポートする名前空間のコンマ区切り一覧。|  
  
## <a name="remarks"></a>コメント  
 `-imports`オプションは、現在のソース ファイルまたは参照先アセンブリのセット内で定義された任意の名前空間をインポートします。  
  
 指定された名前空間内のメンバー`-imports`コンパイルですべてのソース コード ファイルに使用します。 使用して、 [Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)を 1 つのソース コード ファイルの名前空間を使用します。  
  
|設定する Visual Studio 統合開発環境ではインポート/|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[参照]** タブをクリックします。<br />3.横にあるボックスに名前空間の名前を入力、**ユーザー インポートの追加**ボタンをクリックします。<br />4.クリックして、**ユーザー インポートの追加**ボタンをクリックします。|  
  
## <a name="example"></a>例  
 次のコードをコンパイル時に`/imports:system.globalization`を指定します。 これがないと正常にコンパイルする必要がありますか、`Imports System.Globalization`ステートメントは、ソース コード ファイルの先頭に含まれること、またはプロパティは、完全に修飾されている`System.Globalization.CultureInfo.CurrentCulture.Name`です。 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
