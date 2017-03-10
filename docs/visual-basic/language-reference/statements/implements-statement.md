---
title: "Implements Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Implements"
  - "Implements"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Implements statement, syntax"
  - "Implements statement"
  - "interface implementation, Implements statement"
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Implements Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

クラスまたは構造体の定義に実装する必要のある、1 つ以上のインターフェイス \(インターフェイス メンバー\) を指定します。  
  
## 構文  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## 指定項目  
 `interfacename`  
 必ず指定します。  インターフェイスを指定します。このインターフェイスのプロパティ、プロシージャ、およびイベントが、クラスまたは構造体の対応するメンバーによって実装されます。  
  
 `interfacemember`  
 必ず指定します。  実装されるインターフェイスのメンバーを指定します。  
  
## 解説  
 インターフェイスは、インターフェイスによってカプセル化されるメンバー \(プロパティ、プロシージャ、およびイベント\) を表すプロトタイプの集合体です。  インターフェイスには、メンバーの宣言だけが含まれます。これらのメンバーを実装するのは、クラスおよび構造体です。  詳細については、「[Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)」を参照してください。  
  
 `Implements` ステートメントは、`Class` ステートメントまたは `Structure` ステートメントの直後に指定する必要があります。  
  
 インターフェイスを実装するときは、インターフェイスで宣言されたメンバーをすべて実装する必要があります。  メンバーのいずれかを省略すると、構文エラーと見なされます。  個々のメンバーを実装するには、クラスまたは構造体にメンバーを宣言するときに、[Implements](../../../visual-basic/language-reference/statements/implements-clause.md) キーワードを \(`Implements` ステートメントとは別に\) 指定します。  詳細については、「[Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)」を参照してください。  
  
 クラスは、プロパティおよびプロシージャを [Private](../../../visual-basic/language-reference/modifiers/private.md) で実装できますが、そうするとクラスのインスタンスをインターフェイスの型で宣言した変数にキャストしない限り、これらのメンバーにアクセスできなくなります。  
  
## 使用例  
 `Implements` ステートメントを使って、インターフェイスのメンバーを実装するコード例を次に示します。  イベント、プロパティ、およびプロシージャを含むインターフェイスが、`ICustomerInfo` という名前で定義されています。  `customerInfo` クラスは、インターフェイスに定義されたすべてのメンバーを実装します。  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/implements-statement_1.vb)]  
  
 `customerInfo` クラスでは 1 行のソース コードに `Implements` ステートメントを定義し、そのクラスが `ICustomerInfo` インターフェイスのすべてのメンバーを実装することを示しています。  その後、クラスの各メンバーにおいて、メンバー宣言に `Implements` キーワードを指定し、そのインターフェイスのメンバーが実装されることを示しています。  
  
## 使用例  
 実装されたインターフェイスを使用する 2 つのプロシージャを次に示します。  インターフェイスの実装をテストするには、これらのプロシージャをプロジェクトに追加して、`testImplements` プロシージャを呼び出します。  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/implements-statement_2.vb)]  
  
## 参照  
 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)