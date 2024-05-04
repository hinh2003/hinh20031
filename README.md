ublic class SalesAnalysis {
    public static void main(String[] args) {
        String driverName = "org.apache.hive.jdbc.HiveDriver";
        String url = "jdbc:hive2://localhost:10000/default";
        String username = "";
        String password = "";

        try {
            Class.forName(driverName);
            Connection conn = DriverManager.getConnection(url, username, password);
            Statement stmt = conn.createStatement();

            // Thực hiện truy vấn Hive để lấy tổng doanh số bán hàng trong mỗi ngày/tháng/năm
            String query = "SELECT DATE_FORMAT(timestamp, 'yyyy-MM-dd') AS sale_date, " +
                           "SUM(quantity * unit_price) AS total_sales " +
                           "FROM transactions " +
                           "GROUP BY DATE_FORMAT(timestamp, 'yyyy-MM-dd')";
            ResultSet rs = stmt.executeQuery(query);

            // In ra kết quả
            System.out.println("Doanh số bán hàng theo ngày:");
            while (rs.next()) {
                String saleDate = rs.getString("sale_date");
                double totalSales = rs.getDouble("total_sales");
                System.out.println(saleDate + ": " + totalSales);
            }

            rs.close();
            stmt.close();
            conn.close();
        } catch (ClassNotFoundException | SQLException e) {
            e.printStackTrace();
        }
    }
