<!-- DataTable.svelte -->
<script>
    let tableData = [
    {
        date: "02/08/2023",
        day: "Monday",
        incomeType: "Cash Deposit",
        description: "ATM Cash Deposit",
        depositType: "Cash/ATM",
        amount: "$150.00"
    },
    {
        date: "02/04/2023",
        day: "Tuesday",
        incomeType: "Cash Deposit",
        description: "ATM Cash Deposit",
        depositType: "Cash/ATM",
        amount: "$60.00"
    },
    {
        date: "02/03/2023",
        day: "Friday",
        incomeType: "Payroll",
        description: "Walmart Payroll PPD 7",
        depositType: "Direct Deposit",
        amount: "$809.00"
    },
    {
        date: "01/20/2023",
        day: "Friday",
        incomeType: "Payroll",
        description: "Walmart Payroll PPD D7",
        depositType: "Direct Deposit",
        amount: "$809.00"
    },
    {
        date: "01/19/2023",
        day: "Thursday",
        incomeType: "Payroll",
        description: "Capital Cinemas Payroll Dep ID 7",
        depositType: "Direct Deposit",
        amount: "$412.00"
    },
    {
        date: "01/01/2023",
        day: "Tuesday",
        incomeType: "Transfer",
        description: "Zele transfer from XXX",
        depositType: "Transfer",
        amount: "$62.00"
    },
    {
        date: "01/06/2023",
        day: "Friday",
        incomeType: "Payroll",
        description: "Walmart Payroll PPD D7",
        depositType: "Direct Deposit",
        amount: "$809.00"
    },
    {
        date: "12/23/2022",
        day: "Friday",
        incomeType: "Payroll",
        description: "Walmart Payroll PPD D7",
        depositType: "Direct Deposit",
        amount: "$809.00"
    },
    {
        date: "12/22/2022",
        day: "Thursday",
        incomeType: "Payroll",
        description: "Capital Cinemas Payroll Dep ID 7",
        depositType: "Direct Deposit",
        amount: "$412.00"
    },
    {
        date: "12/09/2022",
        day: "Friday",
        incomeType: "Payroll",
        description: "Walmart Payroll PPD ID.",
        depositType: "Direct Deposit",
        amount: "$809.00"
    },
    {
        date: "11/24/2022",
        day: "Thursday",
        incomeType: "Payroll",
        description: "Capital Cinemas Payroll Dep ID 7",
        depositType: "Direct Deposit",
        amount: "$412.00"
    },
    {
        date: "11/16/2022",
        day: "Sunday",
        incomeType: "Check Deposit",
        description: "Remote Online Deposit",
        depositType: "Online Deposit",
        amount: "$544.64"
    },
    {
        date: "10/19/2022",
        day: "Monday",
        incomeType: "Benefits",
        description: "US Dep treasure.",
        depositType: "Direct Deposit",
        amount: "$3100.00"
    }
]
    // $: total = tableData.reduce((total,curr)=>(total = total + Number(currency.replace(/[^0-9.-]+/g,""));),0)
    // let tableData = [
    //   {
    //     Name: "Tiger Nixon",
    //     Position: "System Architect",
    //     Office: "Edinburgh",
    //     Age: 61,
    //     "Start date": "2011/04/25",
    //     Salary: "$320,800"
    //   },
    //   {
    //   Name: "Garrett Winters",
    //   Position: "Accountant",
    //   Office: "Tokyo",
    //   Age: "63",
    //   "Start date": "2011/07/25",
    //   Salary: "$170,750"
    // },
    // {
    //   Name: "Ashton Cox",
    //   Position: "Junior Technical Author",
    //   Office: "San Francisco",
    //   Age: "66",
    //   "Start date": "2009/01/12",
    //   Salary: "$186,000"
    // },
    // {
    //   Name: "Cedric Kelly",
    //   Position: "Senior Javascript Developer",
    //   Office: "Edinburgh",
    //   Age: "22",
    //   "Start date": "2012/03/29",
    //   Salary: "$433,060"
    // },
    // {
    //   Name: "Airi Satou",
    //   Position: "Accountant",
    //   Office: "Tokyo",
    //   Age: "33",
    //   "Start date": "2008/11/28",
    //   Salary: "$162,700"
    // },
    // {
    //   Name: "Brielle Williamson",
    //   Position: "Integration Specialist",
    //   Office: "New York",
    //   Age: "23",
    //   "Start date": "2012/12/02",
    //   Salary: "$372,000"
    // }
    // ];
  

  let sortBy = null;
  let sortOrder = 1;

  // dropdown
  let IncomeSource = 'all';

  let transactionType = getUniqueTransactionType();
  let uniqueMonth = getUniqueMonth();
  let uniqueDepositDay = getUniqueDepositDay();
  let uniqueDeositType = getUniqueDeositType();
  let uniqueIncomeTypes = getUniqueIncomeTypes();
  let uniqueIncomeSources = getUniqueIncomeSources();



  function getUniqueTransactionType() {
      const days = tableData.map(item => item.description);
      return [...new Set(days)];
  }
  function getUniqueMonth() {
      // const days = tableData.map(item => item.date);
      // return [...new Set(days)];

      const months = tableData.map(item => {
          const [month, day, year] = item.date.split('/');
          return `${getMonthName(parseInt(month))} ${year}`;
      });
      return [...new Set(months)];
  }
  function getUniqueDepositDay() {
      const amounts = tableData.map(item => item.day);
      return [...new Set(amounts)];
  }
  function getUniqueDeositType() {
      const amounts = tableData.map(item => item.depositType);
      return [...new Set(amounts)];
  }
  function getUniqueIncomeTypes() {
      const incomeTypes = tableData.map(item => item.incomeType);
      return [...new Set(incomeTypes)];
  }
  function getUniqueIncomeSources() {
      const sources = tableData.map(item => item.description);
      return [...new Set(sources)];
  }



  function sortData(columnName) {
    if (sortBy === columnName) {
      sortOrder *= -1;
    } else {
      sortBy = columnName;
      sortOrder = 1;
    }

    tableData = [...tableData].sort((a, b) => {
      const valueA = a[columnName];
      const valueB = b[columnName];
      return sortOrder * (valueA < valueB ? -1 : 1);
    });
  }
  function getMonthName(monthNumber) {
        const monthNames = [
            'January', 'February', 'March', 'April', 'May', 'June',
            'July', 'August', 'September', 'October', 'November', 'December'
        ];
        return monthNames[monthNumber - 1];
    }
  // $: totaAmount = tableData.reduce((total,curr)=>(total = total + curr.amount),0) //normal format
  // Function to parse and calculate the total amount:
  $: totalAmount = tableData.reduce((total, curr) => {
    const amount = parseFloat(curr.amount.replace(/\$/g, '').replace(/,/g, ''));
    return total + amount;
  }, 0);
</script>

<h2 class="mb-3">All Transactions |</h2>
<label for="">Transaction Type:
  <select name="" id="">
    <option value="all">All</option>
    {#each transactionType as transaction}
      <option value={transaction}>{transaction}</option>
    {/each}
  </select>
</label>

<label for="">Month:
  <select name="" id="">
    <option value="all">All</option>
    {#each uniqueMonth as month}
      <option value={month}>{month}</option>
    {/each}
  </select>
</label>
<label for="">Deposit Day:
  <select name="" id="">
    <option value="all">All</option>
    {#each uniqueDepositDay  as depositDay}
      <option value={depositDay}>{depositDay}</option>
    {/each}
  </select>
</label>

<label for="">Deposit Type:
  <select name="" id="">
    <option value="all">All</option>
    {#each uniqueDeositType as deositType}
      <option value={deositType}>{deositType}</option>
    {/each}
  </select>
</label>

<label for="">Income Type:
  <select name="" id="">
    <option value="all">All</option>
    {#each uniqueIncomeTypes as incomeType}
      <option value={incomeType}>{incomeType}</option>
    {/each}
  </select>
</label>

<label for="">Income source::
  <select name="" id="">
    <option value="all">All</option>
    {#each uniqueIncomeSources as IncomeSources}
      <option value={IncomeSources}>{IncomeSources}</option>
    {/each}
  </select>
</label>


<table class="table">
  <thead class="bg">
    <tr>
      <th class="th-sm tableHeader" on:click={() => sortData("date")}>Deposit Date {sortBy === "date" ? (sortOrder === 1 ? "▲" : "▼") : ""}</th>
      <th class="th-sm tableHeader" on:click={() => sortData("day")}>Deposit Day {sortBy === "day" ? (sortOrder === 1 ? "▲" : "▼") : ""}</th>
      <th class="th-sm tableHeader" on:click={() => sortData("incomeType")}>Income Type {sortBy === "incomeType" ? (sortOrder === 1 ? "▲" : "▼") : ""}</th>
      <th class="th-sm tableHeader" on:click={() => sortData("description")}>Income Description {sortBy === "description" ? (sortOrder === 1 ? "▲" : "▼") : ""}</th>
      <th class="th-sm tableHeader" on:click={() => sortData("depositType")}>Deposit Type {sortBy === "depositType" ? (sortOrder === 1 ? "▲" : "▼") : ""}</th>
      <th class="th-sm tableHeader" on:click={() => sortData("amount")}>Deposit Amount {sortBy === "amount" ? (sortOrder === 1 ? "▲" : "▼") : ""}</th>
    </tr>
  </thead>
  <tbody>
    {#each tableData as item (item.date)}
      <tr>
        <td>{item.date}</td>
        <td>{item.day}</td>
        <td>{item.incomeType}</td>
        <td>{item.description}</td>
        <td>{item.depositType}</td>
        <td class="text-success">{item.amount}</td>
      </tr>
    {/each}
    <!-- <tr><td>Amount:$500</td></tr> -->
  </tbody>
  <tbody class="text-success thick">Total: {totalAmount}</tbody>
  <!-- <tbody class="text-success">Total: $452.25</tbody> -->
</table>

<style>
    .bg{
        background-color: aqua;
    }
    tbody.thick {
      font-weight: bold;
    }
    .tableHeader{
      background-color: rgb(54, 50, 50);
      color: aliceblue;
    }
</style>
  