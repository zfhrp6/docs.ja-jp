---
title: "/libpath |Microsoft ドキュメント"
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
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: 16
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
ms.openlocfilehash: cc534e782cff34f0c4882f3da2af973fed69ff80
ms.lasthandoff: 03/13/2017

---
# <a name="libpath"></a>/libpath
参照先アセンブリの場所を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`dirList`|必須です。 コンパイラが参照先アセンブリを探す場合にディレクトリのセミコロン区切りのリストが見つからないいずれかで現在の作業ディレクトリ (コンパイラの起動元ディレクトリ) または共通言語ランタイムのシステム ディレクトリ。 ディレクトリ名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。|  
  
## <a name="remarks"></a>コメント  
 `/libpath`オプションによって参照されるアセンブリの場所を指定する、 [/reference](../../../visual-basic/reference/command-line-compiler/reference.md)オプション。  
  
 コンパイラは、次の順序で完全に修飾されていないアセンブリ参照を検索します。  
  
1.  現在の作業ディレクトリです。 これは、コンパイラが呼び出されているディレクトリです。  
  
2.  共通言語ランタイムのシステム ディレクトリ。  
  
3.  指定したディレクトリ`/libpath`します。  
  
4.  LIB 環境変数で指定したディレクトリです。  
  
 `/libpath`オプションが加法; を指定するには、前の値に&1; 回追加よりも詳細です。  
  
 使用`/reference`アセンブリ参照を指定します。  
  
|統合開発環境 Visual Studio で/libpath を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.クリックして、**参照** タブをクリックします。<br />3.クリックして、**パスを参照しています.**  ボタンをクリックします。<br />4.**参照パス** ダイアログ ボックスで、ディレクトリ名を入力、**フォルダー:**ボックス。<br />5.クリックして**フォルダーを追加する**です。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`.exe ファイルを作成します。 コンパイラは、アセンブリ参照の作業ディレクトリで、c: ドライブのルート ディレクトリ、および c: ドライブのアセンブリの新しいディレクトリを検索します。  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
