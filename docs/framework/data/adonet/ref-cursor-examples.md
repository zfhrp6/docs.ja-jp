---
title: REF CURSOR の例
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: 9593a30524b7d8161903b840e1bdb0ee007027a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353548"
---
# <a name="ref-cursor-examples"></a><span data-ttu-id="eb639-102">REF CURSOR の例</span><span class="sxs-lookup"><span data-stu-id="eb639-102">REF CURSOR Examples</span></span>
<span data-ttu-id="eb639-103">REF CURSOR の例は、REF CURSOR の使い方を説明する、次の 3 つの Microsoft Visual Basic の例によって構成されています。</span><span class="sxs-lookup"><span data-stu-id="eb639-103">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="eb639-104">サンプル</span><span class="sxs-lookup"><span data-stu-id="eb639-104">Sample</span></span>|<span data-ttu-id="eb639-105">説明</span><span class="sxs-lookup"><span data-stu-id="eb639-105">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb639-106">OracleDataReader の REF CURSOR パラメーター</span><span class="sxs-lookup"><span data-stu-id="eb639-106">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="eb639-107">この例では、REF CURSOR パラメーターを返し、<xref:System.Data.OracleClient.OracleDataReader> として値を読み込む PL/SQL ストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="eb639-107">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="eb639-108">OracleDataReader を使用した複数の REF CURSOR からのデータの取得</span><span class="sxs-lookup"><span data-stu-id="eb639-108">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="eb639-109">この例は、2 つの REF CURSOR パラメーターを返しを使用して値を読み取る、PL/SQL ストアド プロシージャを実行、 **OracleDataReader**です。</span><span class="sxs-lookup"><span data-stu-id="eb639-109">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="eb639-110">1 つまたは複数の REF CURSOR を使用した DataSet の値の設定</span><span class="sxs-lookup"><span data-stu-id="eb639-110">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="eb639-111">この例では、2 つの REF CURSOR パラメーターを返し、返された行を <xref:System.Data.DataSet> に入力する PL/SQL ストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="eb639-111">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="eb639-112">これらの例を使用するには、必要に応じて Oracle テーブルを作成し、さらに PL/SQL パッケージとパッケージ本体を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb639-112">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="eb639-113">Oracle テーブルの作成</span><span class="sxs-lookup"><span data-stu-id="eb639-113">Creating the Oracle Tables</span></span>  
 <span data-ttu-id="eb639-114">これらの例では、Oracle Scott/Tiger スキーマで定義されたテーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="eb639-114">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="eb639-115">Oracle Scott/Tiger スキーマは、ほとんどの Oracle のインストールに含まれています。</span><span class="sxs-lookup"><span data-stu-id="eb639-115">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="eb639-116">このスキーマが含まれていない場合は、{OracleHome}\rdbms\admin\scott.sql にある SQL コマンド ファイルを使用して、これらの例で使用されているテーブルとインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="eb639-116">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="eb639-117">Oracle パッケージとパッケージ本体の作成</span><span class="sxs-lookup"><span data-stu-id="eb639-117">Creating the Oracle Package and Package Body</span></span>  
 <span data-ttu-id="eb639-118">これらの例では、次の PL/SQL パッケージとパッケージ本体がサーバー上に必要になります。</span><span class="sxs-lookup"><span data-stu-id="eb639-118">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="eb639-119">次の Oracle パッケージを Oracle サーバー上に作成します。</span><span class="sxs-lookup"><span data-stu-id="eb639-119">Create the following Oracle package on the Oracle server.</span></span>  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
    TYPE T_CURSOR IS REF CURSOR;   
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,   
                               IO_CURSOR IN OUT T_CURSOR);   
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/   
```  
  
 <span data-ttu-id="eb639-120">Oracle サーバーで、次の Oracle パッケージ本体を作成します。</span><span class="sxs-lookup"><span data-stu-id="eb639-120">Create the following Oracle package body on the Oracle server.</span></span>  
  
```  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS  
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,  
                               IO_CURSOR IN OUT T_CURSOR)  
    IS   
        V_CURSOR T_CURSOR;   
    BEGIN   
        IF N_EMPNO <> 0   
        THEN  
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO   
                  AND EMP.EMPNO = N_EMPNO;  
  
        ELSE   
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO;  
  
        END IF;  
        IO_CURSOR := V_CURSOR;   
    END OPEN_ONE_CURSOR;   
  
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,  
                                DEPTCURSOR OUT T_CURSOR)  
    IS   
        V_CURSOR1 T_CURSOR;   
        V_CURSOR2 T_CURSOR;   
    BEGIN   
        OPEN V_CURSOR1 FOR SELECT * FROM EMP;  
        OPEN V_CURSOR2 FOR SELECT * FROM DEPT;  
        EMPCURSOR  := V_CURSOR1;   
        DEPTCURSOR := V_CURSOR2;   
    END OPEN_TWO_CURSORS;   
END CURSPKG;  
/  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb639-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb639-121">See Also</span></span>  
 [<span data-ttu-id="eb639-122">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="eb639-122">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [<span data-ttu-id="eb639-123">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="eb639-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
