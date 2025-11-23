CREATE FUNCTION fn_GetRemainingSeats (@CourseCode VARCHAR(10))
RETURNS INT
AS
BEGIN
    DECLARE @Capacity SMALLINT;
    DECLARE @EnrolledCount INT;
    DECLARE @Remaining INT;

    --get the max capacity from course table
    SELECT @Capacity = Capacity 
    FROM Course.Course 
    WHERE CourseCode = @CourseCode;

    --count how many students are currently enrolled (if completed =0 they are currently taking it)
    SELECT @EnrolledCount = COUNT(*)
    FROM Std.Enrollment
    WHERE CourseCode = @CourseCode 
    AND Completed = 0;

    --calculate remaining seats
    SET @Remaining = @Capacity - @EnrolledCount;

    --return 0 if calculation is -ve (just in case)
    IF @Remaining < 0 SET @Remaining = 0;

    RETURN @Remaining;
END;
GO
