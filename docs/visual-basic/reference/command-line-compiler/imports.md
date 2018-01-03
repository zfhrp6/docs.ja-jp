---
title: /imports (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cdb7cff2221930113d6b49a640da0844f175f1b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="imports-visual-basic"></a>/imports (Visual Basic)
指定したアセンブリから名前空間をインポートします。  
  
## <a name="syntax"></a>構文  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`namespaceList`|必須。 インポートする名前空間のコンマ区切り一覧。|  
  
## <a name="remarks"></a>コメント  
 `/imports`オプションは、現在のソース ファイルまたは参照先アセンブリのセット内で定義された任意の名前空間をインポートします。  
  
 指定された名前空間内のメンバー`/imports`コンパイルですべてのソース コード ファイルに使用します。 使用して、 [Imports ステートメント (.NET Namespace よぶ型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)を 1 つのソース コード ファイルの名前空間を使用します。  
  
|設定する Visual Studio 統合開発環境ではインポート/|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[参照]** タブをクリックします。<br />3.横にあるボックスに名前空間の名前を入力、**ユーザー インポートの追加**ボタンをクリックします。<br />4.クリックして、**ユーザー インポートの追加**ボタンをクリックします。|  
  
## <a name="example"></a>例  
 次のコードをコンパイル時に`/imports:system`を指定します。  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a>参照  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
