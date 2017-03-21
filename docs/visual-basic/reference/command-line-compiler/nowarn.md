---
title: "/nowarn |Microsoft ドキュメント"
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
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: 15
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
ms.openlocfilehash: 61b145a9eb95f5357c7aa2983a96c31e8f2cef6a
ms.lasthandoff: 03/13/2017

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
|`numberList`|省略可能です。 しないか、コンパイラの警告の ID 番号のコンマ区切りリスト。 警告の Id が指定されていない場合、すべての警告は抑制されます。|  
  
## <a name="remarks"></a>コメント  
 `/nowarn`オプションは、コンパイラの警告が発生しないようにします。 個々 の警告を抑制するのに警告の ID を提供、`/nowarn`コロンの後ろのオプションです。 複数の警告番号コンマで区切ります。  
  
 警告 id の数値の一部だけを指定する必要があります。 ある BC42024、未使用のローカル変数に対して警告を抑制する場合の指定など`/nowarn:42024`します。  
  
 警告 ID 番号の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。  
  
|統合開発環境 Visual Studio で/nowarn を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.**[コンパイル]** タブをクリックします。<br />3.選択、**すべての警告を無効にする**をすべての警告を無効にする チェック ボックスです。<br />     または<br />     特定の警告を無効にするには、**なし**警告の横にあるドロップダウン リストからです。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`すべての警告は表示されません。  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`と、使用されていないローカル変数 (42024) に警告が表示されません。  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)
