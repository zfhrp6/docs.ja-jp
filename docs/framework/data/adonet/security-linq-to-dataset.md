---
title: セキュリティ (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: 43d529b6f74b58783cc2aaa7a81b2f75790b4e40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364962"
---
# <a name="security-linq-to-dataset"></a>セキュリティ (LINQ to DataSet)
このトピックでは、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] におけるセキュリティの問題について説明します。  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>信頼できないコンポーネントへのクエリの受け渡し  
 A[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリをプログラムの 1 つのポイントで策定されたして、別の実行できることができます。 このクエリは、それが定義されている場所から見えるすべての要素、たとえば、呼び出し元のメソッドが所属しているクラスのプライベート メンバーやローカル変数/引数を表すシンボルなどを参照できます。 実行時には、呼び出し元のコードから見えなくても、クエリの定義時に参照されたメンバーであれば、事実上アクセスできることになります。 クエリを実行するコードが、任意に見える要素を増やすことはできません。つまり、アクセスできる範囲を実行元のコードそのものが決めることはできません。 アクセスの範囲は、クエリがアクセスできる範囲に限定されており、そのクエリ自体を通してのみアクセスできます。  
  
 つまり、クエリへの参照をコードの別の部分に渡した場合、そのクエリを受け取ったコンポーネントが信頼され、パブリックであるか、プライベートであるかに関係なく、クエリによって参照されたすべてのメンバーに対するアクセスが許可されます。 一般に、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]非公開にする必要がある情報を公開しないように、クエリを慎重に作成されている場合を除き、クエリを信頼されていないコンポーネントに渡されなかった必要があります。  
  
## <a name="external-input"></a>外部入力  
 アプリケーションによっては (ユーザーや他の外部エージェントからの) 外部入力を受け取り、その入力内容に応じた処理を実行する場合があります。  場合、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]アプリケーションが特定の方法で、外部入力または使用する外部のクエリの入力に基づくクエリを構築可能性があります。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリでは、リテラルを渡すことのできる場所であればどこででもパラメーターを渡すことができます。 アプリケーションの開発者は、外部エージェントから受け取ったリテラルを直接クエリに挿入することは避け、パラメーター化クエリを使用するようにしてください。  
  
 直接、間接を問わず、ユーザーまたは外部エージェントから受け取った入力には、対象言語の構文を巧みに利用して不正なアクションを実行する内容が含まれている可能性があります。 これは、対象言語が Transact-SQL である場合、その攻撃パターンにちなんで SQL インジェクション攻撃と呼ばれます。 クエリに直接挿入されるユーザー入力を使用して、データベースのテーブルを削除したり、サービス拒否の状態を引き起こしたり、本来実行される操作を改変したりします。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 内でクエリを構築することは可能ですが、オブジェクト モデルの API を介して構築します。 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリが TRANSACT-SQL では、従来の感覚で SQL インジェクション攻撃を受ける可能性がない文字列操作や文字列連結を使用して、構成されていません。  
  
## <a name="see-also"></a>関連項目  
 [プログラミング ガイド](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
