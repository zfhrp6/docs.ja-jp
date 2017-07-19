---
title: "Security (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Security (LINQ to DataSet)
このトピックでは、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] におけるセキュリティの問題について説明します。  
  
## 信頼できないコンポーネントへのクエリの受け渡し  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリはプログラム内のどこか 1 か所で定義されていれば、別の場所から実行できます。  このクエリは、それが定義されている場所から見えるすべての要素、たとえば、呼び出し元のメソッドが所属しているクラスのプライベート メンバーやローカル変数\/引数を表すシンボルなどを参照できます。  実行時には、呼び出し元のコードから見えなくても、クエリの定義時に参照されたメンバーであれば、事実上アクセスできることになります。  クエリを実行するコードが、任意に見える要素を増やすことはできません。つまり、アクセスできる範囲を実行元のコードそのものが決めることはできません。  アクセスの範囲は、クエリがアクセスできる範囲に限定されており、そのクエリ自体を通してのみアクセスできます。  
  
 つまり、クエリへの参照をコードの別の部分に渡した場合、そのクエリを受け取ったコンポーネントが信頼され、パブリックであるか、プライベートであるかに関係なく、クエリによって参照されたすべてのメンバーに対するアクセスが許可されます。  クエリが慎重に作成され、機密情報が決して漏洩しないという確信がない限り、通常は [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] のクエリを信頼できないコンポーネントに渡さないでください。  
  
## 外部入力  
 アプリケーションによっては \(ユーザーや他の外部エージェントからの\) 外部入力を受け取り、その入力内容に応じた処理を実行する場合があります。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] のケースで言えば、アプリケーションが外部入力を基に \(またはクエリ内で外部入力を使用して\)、決められた方法でクエリを構築することが考えられます。[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] のクエリは、リテラル値を使用できる部分に記述されていれば、どのようなパラメーターでも受け取ります。  アプリケーションの開発者は、外部エージェントから受け取ったリテラルを直接クエリに挿入することは避け、パラメーター化クエリを使用するようにしてください。  
  
 直接、間接を問わず、ユーザーまたは外部エージェントから受け取った入力には、対象言語の構文を巧みに利用して不正なアクションを実行する内容が含まれている可能性があります。  これは、対象言語が Transact\-SQL である場合、その攻撃パターンにちなんで SQL インジェクション攻撃と呼ばれます。  クエリに直接挿入されるユーザー入力を使用して、データベースのテーブルを削除したり、サービス拒否の状態を引き起こしたり、本来実行される操作を改変したりします。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 内でクエリを構築することは可能ですが、オブジェクト モデルの API を介して構築します。Transact\-SQL におけるクエリの作成とは異なり、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] のクエリが、文字列操作や文字列連結によって構築されることはありません。その意味では、SQL インジェクション攻撃に十分な抵抗力を持っていると言えます。  
  
## 参照  
 [Programming Guide](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)