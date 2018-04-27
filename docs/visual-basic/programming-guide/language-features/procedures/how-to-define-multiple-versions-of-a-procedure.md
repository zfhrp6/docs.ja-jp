---
title: '方法: プロシージャの複数のバージョンを定義する (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6db075e9b31355d4a0a593040b1fe7c96a0c730
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>方法: プロシージャの複数のバージョンを定義する (Visual Basic)
によって複数のバージョンのプロシージャを定義できます*オーバー ロード*バージョンごとに異なるパラメーター リストは、同じ名前を使用しています。 オーバー ロードの目的では、名前で区別することがなく密接に関連するいくつかのバージョンのプロシージャを定義します。  
  
 詳細については、次を参照してください。[プロシージャのオーバー ロード](./procedure-overloading.md)です。  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>プロシージャの複数のバージョンを定義するには  
  
1.  書き込み、`Sub`または`Function`を定義する手順の各バージョンの宣言ステートメントです。 すべての宣言で同じプロシージャ名を使用します。  
  
2.  前に、`Sub`または`Function`を含む各宣言でキーワード、 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワード。 省略可能`Overloads`宣言のいずれかに含める場合は、宣言に含める必要がありますすべての宣言でします。  
  
3.  次の各宣言ステートメントには、呼び出し元のコードがそのバージョンのパラメーター リストに一致する引数を指定する、特定のケースを処理する手順のコードを記述します。 必要はありませんをテストする呼び出し元のコードが提供するパラメーターです。 Visual Basic では、プロシージャの対応するバージョンに制御を渡します。  
  
4.  使用してプロシージャの各バージョンの終了、`End Sub`または`End Function`に応じてステートメントです。  
  
## <a name="example"></a>例  
 次の例では定義、`Sub`顧客の残高に対してトランザクションをポストするプロシージャ。 使用して、`Overloads`して名前と、他のアカウント番号によって、顧客が使用できるプロシージャの 2 つのバージョンを定義するキーワードです。  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 呼び出し元のコードは、いずれかとして、顧客 id を取得できます、`String`または`Integer`、およびどちらの場合、同じ呼び出し元ステートメントを使用します。  
  
 これらのバージョンを呼び出す方法については、`post`プロシージャを参照してください[する方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)です。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 プロシージャ名が同じで、異なるパラメーター リストを持つ、オーバー ロードされたバージョンを確認します。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [プロシージャのトラブルシューティング](./troubleshooting-procedures.md)  
 [方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)  
 [オーバーロードの解決](./overload-resolution.md)
