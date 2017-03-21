---
title: "/main |Microsoft ドキュメント"
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
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: 19
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
ms.openlocfilehash: dded7621845141896f353d69ab757010c825b975
ms.lasthandoff: 03/13/2017

---
# <a name="main"></a>/main
クラスまたはモジュールを含む指定、`Sub Main`プロシージャです。  
  
## <a name="syntax"></a>構文  
  
```  
/main:location  
```  
  
## <a name="arguments"></a>引数  
 `location`  
 必須です。 クラスまたは含まれているモジュールに完全に修飾、`Sub Main`プログラムの開始時に呼び出されるプロシージャです。 フォームの可能性があります**/main:module**または**/main:namespace.module**します。  
  
## <a name="remarks"></a>コメント  
 実行可能ファイルまたは Windows 実行可能プログラムを作成するときに、このオプションを使用します。 場合、 **/main**オプションを省略すると、コンパイラは有効な共有検索`Sub Main`のすべてのパブリック クラスおよびモジュールにします。  
  
 参照してください[Visual Basic の Main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)のさまざまな形式の詳細について、`Main`プロシージャです。  
  
 `location`から継承するクラスは、 <xref:System.Windows.Forms.Form>、コンパイラは、既定値を用意`Main`クラスを持たない場合に、アプリケーションを開始するプロシージャ`Main`プロシージャ</xref:System.Windows.Forms.Form>。 これにより、開発環境で作成されたコマンド ラインでコードをコンパイルできます。  
  
 [!code-vb[VbVbalrCompiler&#16;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a>統合開発環境 Visual Studio で/main を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。  
  
     詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **[アプリケーション]** タブをクリックします。  
  
3.  確認、**アプリケーション フレームワークを有効にする** チェック ボックスをオフになっています。  
  
4.  値を変更、**スタートアップ オブジェクト**ボックス。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`と`T3.vb`を指定している、`Sub Main`手順が記載されて、`Test2`クラスです。  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [NIB: Visual Basic バージョンこんにちは, World の](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)   
 [Visual Basic の main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
