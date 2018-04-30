### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a><span data-ttu-id="b61f1-101">SqlBulkCopy 对字符串使用目标列编码</span><span class="sxs-lookup"><span data-stu-id="b61f1-101">SqlBulkCopy uses destination column encoding for strings</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b61f1-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="b61f1-102">Details</span></span>|<span data-ttu-id="b61f1-103">将数据插入列中时，<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> 使用目标列的编码而不是 <code>VARCHAR</code> 和 <code>CHAR</code> 类型的默认编码。</span><span class="sxs-lookup"><span data-stu-id="b61f1-103">When inserting data into a column, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> uses the encoding of the destination column rather than the default encoding for <code>VARCHAR</code> and <code>CHAR</code> types.</span></span> <span data-ttu-id="b61f1-104">在目标列未使用默认编码时，此更改会消除使用此默认编码所引起的数据损坏的可能性。</span><span class="sxs-lookup"><span data-stu-id="b61f1-104">This change eliminates the possibility of data corruption caused by using the default encoding when the destination column does not use the default encoding.</span></span> <span data-ttu-id="b61f1-105">在极少数情况下，如果对编码进行的更改所生成的数据过大而无法适应目标列，则现有应用程序可能会引发 SqlException 异常。</span><span class="sxs-lookup"><span data-stu-id="b61f1-105">In rare cases, an existing application may throw a SqlException exception if the change in encoding produces data that is too big to fit into the destination column.</span></span>|
|<span data-ttu-id="b61f1-106">建议</span><span class="sxs-lookup"><span data-stu-id="b61f1-106">Suggestion</span></span>|<span data-ttu-id="b61f1-107"><xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> 应不再因为编码差异而损坏数据。</span><span class="sxs-lookup"><span data-stu-id="b61f1-107">Expect that <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=name> will no longer corrupt data due to encoding differences.</span></span> <span data-ttu-id="b61f1-108">如果复制了接近目标列大小限制的字符串，那么可能需要预编码数据（复制该数据以检查数据是否适合目标列）或者捕获 <xref:System.Data.SqlClient.SqlException?displayProperty=name>。</span><span class="sxs-lookup"><span data-stu-id="b61f1-108">If strings near the destination column's size limit are being copied, it may be necessary to either pre-encode data (to be copied to check that the data will fit in the destination column) or catch <xref:System.Data.SqlClient.SqlException?displayProperty=name>s.</span></span>|
|<span data-ttu-id="b61f1-109">范围</span><span class="sxs-lookup"><span data-stu-id="b61f1-109">Scope</span></span>|<span data-ttu-id="b61f1-110">边缘</span><span class="sxs-lookup"><span data-stu-id="b61f1-110">Edge</span></span>|
|<span data-ttu-id="b61f1-111">版本</span><span class="sxs-lookup"><span data-stu-id="b61f1-111">Version</span></span>|<span data-ttu-id="b61f1-112">4.5</span><span class="sxs-lookup"><span data-stu-id="b61f1-112">4.5</span></span>|
|<span data-ttu-id="b61f1-113">类型</span><span class="sxs-lookup"><span data-stu-id="b61f1-113">Type</span></span>|<span data-ttu-id="b61f1-114">运行时</span><span class="sxs-lookup"><span data-stu-id="b61f1-114">Runtime</span></span>|
|<span data-ttu-id="b61f1-115">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="b61f1-115">Affected APIs</span></span>|<ul><li><xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)?displayProperty=nameWithType></li></ul>|
