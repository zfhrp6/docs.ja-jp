---
title: "Auto-Implemented Properties (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.AutoProperty"
  - "vb.AutoImplementedProperty"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "properties [Visual Basic], auto-implemented"
  - "properties, auto-implemented [Visual Basic]"
  - "auto-implemented properties [Visual Basic]"
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Auto-Implemented Properties (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

*自動実装プロパティ*を使用すると、プロパティを `Get` および `Set` するコードを記述することなく、クラスのプロパティをすばやく指定することができます。  自動実装プロパティのコードを記述する場合、Visual Basic コンパイラでは、関連付けられた `Get` プロシージャおよび `Set` プロシージャが作成されるだけでなく、プロパティの変数を格納するためのプライベート フィールドが自動的に作成されます。  
  
 自動実装プロパティを使用することで、プロパティを既定値も含めて 1 つの行で宣言できます。  次に、プロパティ宣言の 3 つの例を示します。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/auto-implemented-properties_1.vb)]  
  
 自動実装プロパティは、プライベート フィールドにプロパティ値が格納されたプロパティに相当します。  自動実装プロパティを次のコード例に示します。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/auto-implemented-properties_2.vb)]  
  
 次のコード例は、前の自動実装プロパティの例で示したコードと同じ結果になります。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/auto-implemented-properties_3.vb)]  
  
 次のコードは、読み取り専用プロパティの実装を示しています。  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
  
```  
  
 例で示されているように、初期化式でプロパティに割り当てることができます。また、含む型のコンストラクター内でプロパティに割り当てることもできます。  任意の時点で読み取り専用プロパティのバッキング フィールドに割り当てることができます。  
  
## バッキング フィールド  
 自動実装プロパティを宣言する場合、Visual Basic では、プロパティ値を格納するための*バッキング フィールド*という隠しプライベート フィールドが自動的に作成されます。  バッキング フィールド名は、自動実装プロパティ名の前にアンダースコア \(\_\) が付いた名前になります。  たとえば、`ID` という名前の自動実装プロパティを宣言した場合は、バッキング フィールド名は `_ID` になります。  同じ `_ID` という名前のクラスのメンバーを含めた場合、名前の競合が発生し、Visual Basic でコンパイル エラーが報告されます。  
  
 また、バッキング フィールドには、次の特性もあります。  
  
-   バッキング フィールドのアクセス修飾子は、そのプロパティ自体に `Public` などの別のアクセス レベルがある場合でも、常に `Private` です。  
  
-   プロパティ フィールドが `Shared` としてマークされている場合は、バッキング フィールドも共有になります。  
  
-   プロパティに指定された属性は、バッキング フィールドには適用されません。  
  
-   バッキング フィールドは、クラス内のコードや、ウォッチ ウィンドウなどのデバッグ ツールからアクセスできます。  ただし、バッキング フィールドは IntelliSense の単語補完リストには表示されません。  
  
## 自動実装プロパティの初期化  
 フィールドの初期化に使用する式は、すべて自動実装プロパティの初期化にも使用できます。  自動実装プロパティを初期化する場合、その式は評価され、そのプロパティの `Set` プロシージャに渡されます。  次のコード例は、初期値を持ついくつかの自動実装プロパティを示しています。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/auto-implemented-properties_4.vb)]  
  
 `Interface` のメンバーである自動実装プロパティ、または `MustOverride` としてマークされた自動実装プロパティを初期化することはできません。  
  
 自動実装プロパティを `Structure` のメンバーとして宣言した場合、自動実装プロパティを `Shared` としてマークした場合にのみ初期化できます。  
  
 自動実装プロパティを配列として宣言した場合、明示的な配列の範囲は指定できません。  しかし、次の例に示すように、配列初期化子を使用して値を指定することができます。  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/auto-implemented-properties_5.vb)]  
  
## 標準構文を必要とするプロパティ定義  
 自動実装プロパティは使いやすく、多くのプログラミング シナリオに対応します。  しかし、自動実装プロパティを使用できない状況もあるため、代わりに標準または*展開された*プロパティ構文を使用する必要があります。  
  
 次のいずれかを実行する場合は、展開されたプロパティ定義構文を使用する必要があります。  
  
-   `Set` プロシージャで受信した値を検証するコードなどのコードを、プロパティの `Get` プロシージャまたは `Set` プロシージャに追加する。  たとえば、電話番号を示す文字列のプロパティ値を設定する前に、その文字列に必要な数の数字が含まれていることを検証する場合です。  
  
-   `Get` プロシージャと `Set` プロシージャに異なるアクセシビリティを指定する。  たとえば、`Set` プロシージャを `Private` にし、`Get` プロシージャを `Public` にする場合です。  
  
-   `WriteOnly` のプロパティを作成する。  
  
-   パラメーター化されたプロパティ \(`Default` プロパティなど\) を使用する。  プロパティのパラメーターを指定するか、`Set` プロシージャに追加のパラメーターを指定するには、展開されたプロパティを宣言する必要があります。  
  
-   バッキング フィールドに属性を指定するか、バッキング フィールドのアクセス レベルを変更する。  
  
-   バッキング フィールドに XML コメントを指定する。  
  
## 自動実装プロパティの展開  
 自動実装プロパティを `Get` プロシージャまたは `Set` プロシージャを含む展開されたプロパティに変換する必要がある場合、Visual Basic コード エディターを使用すると、`Get` プロシージャおよび `Set` プロシージャと、そのプロパティの `End Property` ステートメントを自動的に生成できます。  `Property` ステートメントの後の空白行にカーソルを置き、「`G`」\(`Get` の G\) または「`S`」\(`Set` の S\) と入力し、Enter キーを押すと、コードが生成されます。  `Property` ステートメントの最後で Enter キーを押すと、読み取り専用のプロパティおよび書き込み専用のプロパティの `Get` プロシージャまたは `Set` プロシージャが Visual Basic コード エディターで自動的に作成されます。  
  
## 参照  
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)   
 [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)   
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)