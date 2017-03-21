---
title: "方法: プロシージャ (Visual Basic) の複数のバージョンを定義する |Microsoft ドキュメント"
ms.custom: 
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
- procedures, defining
- Visual Basic code, procedures
- procedures, overloading
- procedures, multiple versions
- procedure overloading, multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
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
ms.openlocfilehash: 0228083ce00a0f552227fd7ae8f0f5a24f65148e
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>方法: プロシージャの複数のバージョンを定義する (Visual Basic)
プロシージャを定義するには、複数のバージョンで*オーバー ロード*バージョンごとに異なるパラメーター リストは、同じ名前を使用しています。 オーバー ロードの目的では、名前で区別することがなく密接に関連するいくつかのバージョンのプロシージャを定義します。  
  
 詳細については、次を参照してください。[プロシージャのオーバー ロード](./procedure-overloading.md)します。  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>プロシージャの複数のバージョンを定義するには  
  
1.  書き込み、`Sub`または`Function`を定義する手順の各バージョンの宣言ステートメントです。 すべての宣言では、同じプロシージャ名を使用します。  
  
2.  前に、`Sub`または`Function`各宣言でキーワード、[オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワードです。 省略可能`Overloads`宣言のいずれかに含める場合は、宣言にする必要がありますに含めるすべての宣言です。  
  
3.  次の各宣言ステートメントには、呼び出し元のコードがそのバージョンのパラメーター リストに一致する引数を提供する特定のケースを処理するプロシージャのコードを記述します。 必要はありませんをテストするパラメーターの呼び出し元のコードが指定されています。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロシージャの対応するバージョンに制御を渡す。  
  
4.  プロシージャの各バージョン、`End Sub`または`End Function`に応じてステートメントです。  
  
## <a name="example"></a>例  
 次の例、`Sub`顧客の残高に対してトランザクションをポストするプロシージャです。 使用して、`Overloads`して名前とその他のアカウント番号によって、顧客が使用できるプロシージャの&2; つのバージョンを定義するキーワードです。  
  
 [!code-vb[VbVbcnProcedures #&72;](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 呼び出し元のコードは、いずれか、顧客 id を取得できます、`String`または`Integer`、どちらの場合も同じステートメントの呼び出しを使用します。  
  
 これらのバージョンを呼び出す方法の詳細について、`post`の手順を参照してください[する方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 プロシージャ名が同じで、異なるパラメーター リストを持つ、オーバー ロードされたバージョンを確認します。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [トラブルシューティングの手順](./troubleshooting-procedures.md)   
 [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md)   
 [オーバーロードの解決](./overload-resolution.md)
