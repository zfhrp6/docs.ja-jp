---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 338b4672d215968275c30d37a2f8061e764aed8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653443"
---
# <a name="-nowarn"></a>-nowarn
警告を生成するコンパイラの機能を無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`numberList`|任意。 コンパイラはしないようにする警告の ID 番号のコンマ区切り一覧。 警告の Id が指定されていない場合、すべての警告は抑制されます。|  
  
## <a name="remarks"></a>コメント  
 `-nowarn`オプションにより、コンパイラの警告を生成しないことができます。 個々 の警告を抑制するのに警告の ID を指定、`-nowarn`コロンの後ろのオプションです。 複数の警告番号をカンマで区切ります。  
  
 警告 id の数値の一部だけを指定する必要があります。 たとえば、BC42024、未使用のローカル変数に対する警告を抑制する場合を指定`-nowarn:42024`です。  
  
 警告 ID 番号の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。  
  
|Visual Studio 統合開発環境で-nowarn を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[コンパイル]** タブをクリックします。<br />3.選択、**すべての警告を無効にする**すべての警告を無効にする チェック ボックスです。<br />     または<br />     特定の警告を無効にするには、 **None**警告の横にあるドロップダウン リストからです。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`し、すべての警告を表示しません。  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`し、使用されていないローカル変数 (42024) に警告を表示しません。  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)
