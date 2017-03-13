---
title: "How to: Reference COM Objects from Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "COM interop, referencing COM objects"
  - "referencing objects, COM objects from Visual Basic"
  - "objects [Visual Basic], referencing"
  - "COM objects, referencing"
  - "interop assemblies"
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Reference COM Objects from Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で、タイプ ライブラリを持つ COM オブジェクトへの参照を追加するには、COM ライブラリの相互運用機能アセンブリを作成する必要があります。  COM オブジェクトのメンバーへの参照は、相互運用機能アセンブリを経由して、実際の COM オブジェクトに転送されます。  COM オブジェクトからの応答は、相互運用機能アセンブリを経由して [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] アプリケーションにルーティングされます。  
  
 COM オブジェクトの型情報を .NET アセンブリに埋め込むと、相互運用機能アセンブリを使用せずに COM オブジェクトを参照できます。  型情報を埋め込むには、COM オブジェクトへの参照の \[`Embed Interop Types`\] プロパティを `True` に設定します。  コマンド ライン コンパイラを使用してコンパイルする場合は、`/link` オプションを使用して COM ライブラリを参照します。  詳細については、「[\/link](../../../visual-basic/reference/command-line-compiler/link.md)」を参照してください。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、統合開発環境 \(IDE: Integrated Development Environment\) でタイプ ライブラリへの参照を追加すると、相互運用機能アセンブリが自動的に作成されます。  コマンド ラインから操作するときは、Tlbimp ユーティリティを使用して、手動で相互運用機能アセンブリを作成できます。  
  
### COM オブジェクトへの参照を追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックし、**\[COM\]** タブをクリックします。  
  
2.  使用するコンポーネントを COM オブジェクトのリストから選択します。  
  
3.  相互運用機能アセンブリへのアクセスを単純化するために、COM オブジェクトを使用するクラスまたはモジュールの先頭に `Imports` ステートメントを追加します。  たとえば、次のコード例では、`Microsoft InkEdit Control 1.0` ライブラリで参照されているオブジェクトの `INKEDLib` 名前空間をインポートします。  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### Tlbimp を使用して相互運用機能アセンブリを作成するには  
  
1.  Tlbimp の格納ディレクトリが検索パスに指定されておらず、格納ディレクトリ以外の作業ディレクトリにいる場合は、Tlbimp の格納ディレクトリを検索パスに追加します。  
  
2.  コマンド プロンプトから Tlbimp を起動し、次の情報を入力します。  
  
    -   タイプ ライブラリを含む DLL の名前と場所  
  
    -   情報を格納する名前空間の名前と場所  
  
    -   作成する相互運用機能アセンブリの名前と場所  
  
     次に例を示します。  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Tlbimp を使用すると、タイプ ライブラリおよび未登録の COM オブジェクトについても相互運用機能アセンブリを作成できます。  ただし、相互運用機能アセンブリを経由して参照される COM オブジェクトは、使用先のコンピューターで正しく登録されている必要があります。  COM オブジェクトを登録するには、Windows オペレーティング システムに付属の Regsvr32 ユーティリティを使用します。  
  
## 参照  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Tlbimp.exe \(タイプ ライブラリ インポーター\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [Tlbexp.exe \(タイプ ライブラリ エクスポーター\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md)   
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)