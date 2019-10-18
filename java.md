package com.startinpoint.uobkh.test.rest;

import java.sql.Connection;
import java.sql.DatabaseMetaData;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;
 
/**
 * This program demonstrates how to establish database connection to Microsoft
 * SQL Server.
 * @author www.codejava.net
 *
 */
public class JdbcSQLServerConnection {
 
    public static void main(String[] args) {
 
        Connection conn = null;
 
        try {
        	try {
				Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
			} catch (ClassNotFoundException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}

            String dbURL = "jdbc:sqlserver://192.168.5.1:1433;databaseName=uobkh_trunk;";
            String user = "devadmin";
            String pass = "P@ger123";
            conn = DriverManager.getConnection(dbURL, user, pass);
            if (conn != null) {
                DatabaseMetaData dm = (DatabaseMetaData) conn.getMetaData();
                System.out.println("Driver name: " + dm.getDriverName());
                System.out.println("Driver version: " + dm.getDriverVersion());
                System.out.println("Product name: " + dm.getDatabaseProductName());
                System.out.println("Product version: " + dm.getDatabaseProductVersion());
            }
 
        } catch (SQLException ex) {
            ex.printStackTrace();
        } finally {
            try {
                if (conn != null && !conn.isClosed()) {
                    conn.close();
                }
            } catch (SQLException ex) {
                ex.printStackTrace();
            }
        }
        
        
        
        
        
        
        
//        Connection conn = null;
//	       
//        try {
//        	try {
//				Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
//			} catch (ClassNotFoundException e) {
//				// TODO Auto-generated catch block
//				e.printStackTrace();
//			}
//
//            String dbURL = "jdbc:sqlserver://192.168.5.1:1433;databaseName=uobkh_trunk;";
//            String user = "devadmin";
//            String pass = "P@ger123";
//            conn = DriverManager.getConnection(dbURL, user, pass);
//            if (conn != null) {
//            	conn.setAutoCommit(false);
//		 		
//		 		PreparedStatement prepStmt = (PreparedStatement) conn.
//		 				prepareStatement("INSERT INTO " +accNoSchemaProps+"." + accountTypeName + " (acc_no,range_id) VALUES(?,?) ");
//		 		 
//		 		long startTime = System.nanoTime();
//		 	
//		 		for (int number : generatedAccNumbers) {
//		 		    prepStmt.setInt(1,number);            
//		 		    prepStmt.setInt(2,createdRangeId);
//		 		    prepStmt.addBatch();
//		 		}
//		 		prepStmt.executeBatch();
//		 		conn.commit();
//		 		long endTime   = System.nanoTime();
//		 		long totalTime = endTime - startTime;
//		 		double elapsedTimeInSecond = (double) totalTime / 1000000000;
//
//		        System.out.println("It takes " +elapsedTimeInSecond + " seconds");
//		 		
//            }
// 
//        } catch (SQLException ex) {
//            ex.printStackTrace();
//        } finally {
//            try {
//                if (conn != null && !conn.isClosed()) {
//                    conn.close();
//                }
//            } catch (SQLException ex) {
//                ex.printStackTrace();
//            }
//        }
        
        
        
        
        
    }
}
