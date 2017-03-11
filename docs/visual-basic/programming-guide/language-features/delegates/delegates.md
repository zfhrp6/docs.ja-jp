---
title: "Delegates (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "02/25/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "delegates [Visual Basic]"
  - "Visual Basic code, delegates"
ms.assetid: 410b60dc-5e60-4ec0-bfae-426755a2ee28
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Delegates (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

デリゲートは、メソッドを参照するオブジェクトです。  デリゲートは他のプログラミング言語で使用される関数ポインターに似ているため、*タイプ セーフ関数ポインター*と説明されることがあります。  しかし、関数のポインターとは異なり、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のデリゲートは、<xref:System.Delegate?displayProperty=fullName> クラスに基づく参照型です。  デリゲートは、共有メソッド \(特定のクラスのインスタンスがなくても呼び出すことのできるメソッド\) とインスタンス メソッドの両方を参照できます。  
  
## デリゲートとイベント  
 デリゲートは、呼び出し側プロシージャと呼び出されるプロシージャの間の媒介手段が必要な状況で役立ちます。  たとえば、イベントを発生させるオブジェクトにおいて、異なる状況で別々のイベント ハンドラーを呼び出すことができるようにする必要があるとします。  ただし、イベントを発生させるオブジェクトでは、どのイベント ハンドラーがどのイベントを処理するかを事前に把握することはできません。  `AddHandler` ステートメントを使用すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によってデリゲートが作成され、イベント ハンドラーを動的にイベントに関連付けることができます。  実行時に、デリゲートによって適切なイベント ハンドラーに呼び出しが転送されます。  
  
 独自のデリゲートを作成することもできますが、ほとんどの場合、デリゲートの作成と詳細の管理は [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によって自動的に行われます。  たとえば、`Event` ステートメントは、`Event` ステートメントを含むクラスの入れ子のクラスとして、`<EventName>EventHandler` という名前のデリゲート クラスを暗黙に定義します。定義の時はイベントと同じシグネチャを使用します。  `AddressOf` ステートメントは、暗黙的に、特定のプロシージャを参照するデリゲートのインスタンスを作成します。  次の 2 つのコード行は等価です。  最初の行では、`Eventhandler` のインスタンスが明示的に作成され、メソッド `Button1_Click` への参照が引数として渡されます。  2 番目の行は、より便利な方法で同じことを実行します。  
  
 [!code-vb[VbVbalrDelegates#6](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/delegates_1.vb)]  
  
 デリゲートの種類をコンパイラでコンテキストから判断できる場合は、簡単なデリゲートの作成方法を使用できます。  
  
## 既存の種類のデリゲートを使用するイベントの宣言  
 状況によっては、基になるデリゲートとして既存の種類のデリゲートを使用するイベントを宣言しなければならない場合があります。  その方法は次のとおりです。  
  
 [!code-vb[VbVbalrDelegates#7](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/delegates_2.vb)]  
  
 これは、同じハンドラーに複数のイベントをルーティングする場合に役立ちます。  
  
## デリゲート変数とパラメーター  
 デリゲートは、フリー スレッド処理や、異なるバージョンの関数を実行時に呼び出す必要のあるプロシージャなど、イベントに関連しない他のタスクにも使用できます。  
  
 たとえば、自動車の名前のリスト ボックスを含む、項目別広告のアプリケーションがあるとします。  広告はタイトルで並べ替えられます。通常、タイトルは自動車の型式です。  問題が発生する可能性があるのは、型式の前に年式が含まれている自動車があるときです。  問題になるのは、リスト ボックスに組み込まれた並べ替え機能の並べ替えの基準が文字コードだけであることです。このため、日付で始まるすべての広告が最初に配置され、その後に型式で始まる広告が配置されます。  
  
 この問題を解決するために、クラスに並べ替えプロシージャを作成できます。このプロシージャは、ほとんどのリスト ボックスに対応する標準的なアルファベット順の並べ替えを使用しますが、実行時に自動車広告用のカスタム並べ替えプロシージャに切り替えることができます。  このプロシージャを作成するには、デリゲートを使用して実行時にカスタム並べ替えプロシージャを並べ替えクラスに渡します。  
  
## AddressOf とラムダ式  
 各デリゲート クラスでは、オブジェクト メソッドの仕様を渡すコンストラクターを定義します。  デリゲート コンストラクターに渡す引数は、メソッドへの参照、またはラムダ式である必要があります。  
  
 メソッドへの参照を指定するには、次の構文を使用します。  
  
 `AddressOf` \[`expression`.\]`methodName`  
  
 コンパイル時の `expression` の型は、シグネチャがデリゲート クラスのシグネチャと同じで、指定された名前のメソッドを持つクラスまたはインターフェイスである必要があります。  `methodName` は、共有メソッドまたはインスタンス メソッドのいずれかにできます。  クラスの既定メソッドに対してデリゲートを作成する場合も、`methodName` は省略できません。  
  
 ラムダ式を指定するには、次の構文を使用します。  
  
 `Function` \(\[`parm` As `type`, `parm2` As `type2`, ...\]\) `expression`  
  
 次の例では、デリゲートの参照を指定するために使用される `AddressOf` 式とラムダ式を示します。  
  
 [!code-vb[VbVbalrDelegates#15](../../../../visual-basic/language-reference/operators/codesnippet/visualbasic/delegates_3.vb)]  
  
 関数のシグネチャは、デリゲート型のシグネチャと一致している必要があります。  ラムダ式の詳細については、「[Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。  デリゲートにラムダ式や `AddressOf` を代入するその他の例については、「[Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)」を参照してください。  
  
## 関連トピック  
  
|Title|Description|  
|-----------|-----------------|  
|[How to: Invoke a Delegate Method](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)|この例では、メソッドとデリゲートを関連付け、デリゲートによってメソッドを呼び出す方法について説明します。|  
|[How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)|デリゲートを使用してプロシージャを別のプロシージャに渡す方法について説明します。|  
|[Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)|シグネチャが一致しない場合でも、Sub や関数をデリゲートやハンドラーに割り当てる方法について説明します。|  
|[Events](../../../../visual-basic/programming-guide/language-features/events/events.md)|Visual Basic のイベントの概要について説明します。|