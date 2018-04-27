---
title: '方法 : Visual Basic から COM オブジェクトを参照する'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f6f7b4887e2cfba65da7a7a890b78c3d6a8508f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>方法 : Visual Basic から COM オブジェクトを参照する
Visual basic でタイプ ライブラリのある COM オブジェクトへの参照を追加する必要があります相互運用機能アセンブリの作成、COM ライブラリの。 COM オブジェクトのメンバーへの参照は、相互運用機能アセンブリにルーティングされ、実際の COM オブジェクトに転送されます。 COM オブジェクトからの応答が相互運用機能アセンブリにルーティングされ、転送、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アプリケーションです。  
  
 .NET アセンブリで COM オブジェクトの型情報を埋め込むことで相互運用機能アセンブリを使用せず、COM オブジェクトを参照できます。 型情報を埋め込むには次のように設定します。、`Embed Interop Types`プロパティを`True`の COM オブジェクトへの参照。 コマンド ライン コンパイラを使用してコンパイルする場合を使用して、 `/link` COM ライブラリを参照するにはオプションです。 詳細については、次を参照してください。 [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)です。  
  
 Visual Basic では、統合開発環境 (IDE) から、タイプ ライブラリへの参照を追加すると、相互運用機能アセンブリが自動的に作成します。 コマンドラインからを使用する場合は、相互運用機能アセンブリを手動で作成する Tlbimp ユーティリティを使用できます。  
  
### <a name="to-add-references-to-com-objects"></a>COM オブジェクトへの参照を追加するには  
  
1.  **プロジェクト** メニューの 選択**参照の追加**をクリックし、 **COM**  ダイアログ ボックスのタブです。  
  
2.  COM オブジェクトの一覧から使用するコンポーネントを選択します。  
  
3.  相互運用機能アセンブリへのアクセスを簡素化するには追加、`Imports`クラスまたは COM オブジェクトを使用するモジュールの先頭にステートメントです。 たとえば、次のコード例は名前空間をインポート`INKEDLib`で参照されるオブジェクトの`Microsoft InkEdit Control 1.0`ライブラリです。  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Tlbimp を使用して相互運用機能アセンブリを作成するには  
  
1.  なっていない、検索パスの一部と、現在では、ディレクトリが配置されている場合は、検索パスに Tlbimp の場所を追加します。  
  
2.  コマンド プロンプトから、次の情報を提供するには、Tlbimp を呼び出します。  
  
    -   タイプ ライブラリを含んでいる DLL の名前と場所  
  
    -   名前と場所、名前空間情報を格納する場所  
  
    -   ターゲットの相互運用機能アセンブリの名前と場所  
  
     次にコード例を示します。  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Tlbimp を使用すると、未登録の COM オブジェクトであっても、タイプ ライブラリの相互運用機能アセンブリを作成します。 しかし、ここで使用するのには、コンピューター上相互運用機能アセンブリによって参照される COM オブジェクトを正しく登録する必要があります。 COM オブジェクトを登録するには、Windows オペレーティング システムに含まれている、Regsvr32 ユーティリティを使用します。  
  
## <a name="see-also"></a>関連項目  
 [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (タイプ ライブラリ エクスポーター)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [チュートリアル : COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [相互運用性のトラブルシューティング](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
