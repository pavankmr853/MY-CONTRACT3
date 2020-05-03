# MY-CONTRACT3
# MAPPING  & NESTED MAPPING

pragma solidity ^0.6.0;

contract MyContract3 {
    //Mapping
    //Mapping in Solidity is seen as hash tables (initialized virtually) with the goal to contain each potential key and map     //it to a value (its byte-representation should consist of zeroes only).
    mapping (uint => string) public names;
    mapping (uint => Book) public books;
    //NestedMapping
    //MAPPING N MAPPING
    mapping(address => mapping (uint => Book))public myBooks;
    
    struct Book {
        string title;
        string author;
    }
        
        constructor() public {
            names[1] = "SEKHAR";
            names[2] = "CHAKRI";
            names[3] = "KARTHIK";
            names[4] = "PARDHU";
            names[5] = "SOMU";
        }
        
        function addBook(uint _id, string memory _title, string memory _author) public {
            books[_id] = Book(_title, _author);
        }
        
        function addMyBook(uint _id, string memory _title, string memory _author) public {
            myBooks[msg.sender][_id] = Book(_title, _author);
        }
}
