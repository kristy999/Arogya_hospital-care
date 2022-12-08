# Arogya_hospital-care
This is a web developing project for a hospital to make their workeasy
Login page
<?php
session_
include('includes/header.php');
if (isset($_SESSION['auth'])) {
$_SESSION['status'] = "You are already logged in";
head
exit(0
});er('Lo
?>
<div cla
>
<div class="container">
<div class="row justify-content-center">
<div class="col-md-5 my-5">
<?php
if (isset($_SESSION['auth_status'])) {
?>
<div class="alert alert-warning alert-dismissible fade show" role="alert">
<strong>Hey!</strong> <?php echo $_SESSION['auth_status']; ?>
<button type="button" class="close" data-dismiss="alert" aria-label="Close">
<span aria-hidden="true">&times;</span>
</button>
</div>
<?php
unset($_SESSION['auth_status']);
}
?>
<?php
include('message.php');
?>
<div class="card my-5">
<div class="card-header bg-dark">
<h5>Login Form</h5>
</div>
<div class="card-body">
<form action="logincode.php" method="POST">
<div class="form-group">
<lable for="">email Id</lable>
<input type="text" name="email" class="form-control" placeholder="Email
Id">
</div>
<div class="form-group">
<lable for="">Password</lable>
<input type="password" name="password" class="form-control"
placeholder="Password">
</div>
<div class="modal-footer">
<button type="submit" name="login_btn" class="btn btn-dark btnblock">Login</button>
<a href="forget_pass.php" class="text-dark">Forget Password?</a>
</div>
</form>
</div>
</div>
</div>
</div>
</div>
</div>
<?php include('includes/script.php'); ?>ss="section"cation: index.php');start();

Patient regiration

<?php
include('config/dbcon.php');
include('authentication.php');
include('includes/header.php');
include('includes/topbar.php');
include('includes/sidebar.php');
?>
<!--Add User Modal -->
<div class="modal fade" id="AddMember" tabindex="-1" aria-labelledby="exampleModalLabel"
aria-hidden="true">
<div class="modal-dialog">
<div class="modal-content">
<div class="modal-header">
<h5 class="modal-title" id="exampleModalLabel">Add Patient</h5>
<button type="button" class="close" data-dismiss="modal" aria-label="Close">
<span aria-hidden="true">&times;</span>
</button>
</div>
<form action="code.php" method="POST">
<div class="modal-body">
<div class="form-group">
<lable for="">Patient Name</lable>
<input type="text" name="patient_name" class="form-control" placeholder="Patient
Name">
</div>
<div class="form-group">
<lable for="">Admission Date</lable>
<input type="date" name="admission_date" class="form-control"
placeholder="Admission Date">
</div>
<div class="form-group">
<lable for="">Ward ID</lable>
<select class="form-control" name="ward_id" class="form-control">
<?php
$query = "SELECT ward_id FROM ward";
$query_run = mysqli_query($con, $query);
if (mysqli_num_rows($query_run) > 0) {
foreach ($query_run as $cnm) {
?>
<option><?= $cnm['ward_id'] ?></option>
<?php
}
} else {
?>
<p>No Record Found</p>
<?php
}
?>
</select>
</div>
<div class="form-group">
<lable for="">Room ID</lable>
<select class="form-control" name="room_id" class="form-control">
<?php
$query = "SELECT room_id FROM room";
$query_run = mysqli_query($con, $query);
if (mysqli_num_rows($query_run) > 0) {
foreach ($query_run as $cnm) {
?>
<option><?= $cnm['room_id'] ?></option>
<?php
}
} else {
?>
<p>No Record Found</p>
<?php
}
?>
</select>
</div>
<div class="form-group">
<lable for="">Phone Number</lable>
<input type="text" name="phone_number" class="form-control"
placeholder="Phone Number">
</div>
</div>
<div class="modal-footer">
<button type="button" class="btn btn-secondary" datadismiss="modal">Close</button>
<button type="submit" name="addPatient" class="btn btn-primary">Save</button>
</div>
</form>
</div>
</div>
</div>
<!-- End Add User Modal -->
<!--Delete User Modal -->
<div class="modal fade" id="DeletModal" tabindex="-1" aria-labelledby="exampleModalLabel"
aria-hidden="true">
<div class="modal-dialog">
<div class="modal-content">
<div class="modal-header">
<h5 class="modal-title" id="exampleModalLabel">Delete Patient Details</h5>
<button type="button" class="close" data-dismiss="modal" aria-label="Close">
<span aria-hidden="true">&times;</span>
</button>
</div>
<form action="code.php" method="POST">
<div class="modal-body">
<input type="hidden" name="delete_id" class="delete_location_id">
<p>
Are you sure. you want to delete this data?
</p>
</div>
<div class="modal-footer">
<button type="button" class="btn btn-secondary" datadismiss="modal">Close</button>
<button type="submit" name="DeletePatient" class="btn btn-primary">Yes,
Delete.!</button>
</div>
</form>
</div>
</div>
</div>
<!-- End Delete User Model-->
<!-- Content Wrapper. Contains page content -->
<div class="content-wrapper">
<section class="content mt-4">
<div class="container">
<div class="row">
<div class="col-md-12">
<?php include('message.php'); ?>
<div class="card">
<div class="card-header">
<h4>
Patient
<a href="" data-toggle="modal" data-target="#AddMember"
class="btn btn-primary float-right">Add Patient</a>
</h4>
</div>
<div class="card-body">
<table class="table table-bordered">
<thead>
<tr>
<th>Partner ID</th>
<th>Patient Name</th>
<th>Admission Date</th>
<th>Discharge Date</th>
<th>Ward ID</th>
<th>Room ID</th>
<th>Phone Number</th>
<th>Edit</th>
<th>Delete</th>
</tr>
</thead>
<tbody>
<?php
$query = "SELECT * FROM patient";
$query_run = mysqli_query($con, $query);
if (mysqli_num_rows($query_run) > 0) {
foreach ($query_run as $cate) {
?>
<tr>
<td><?= $cate['patient_id'] ?></td>
<td><?= $cate['patient_name'] ?></td>
<td><?= $cate['admission_date'] ?></td>
<td><?= $cate['discharge_date'] ?></td>
<td><?= $cate['ward_id'] ?></td>
<td><?= $cate['room_id'] ?></td>
<td><?= $cate['phone_number'] ?></td>
<td>
<a href="patient-edit.php?patient_id=<?php echo $cate['patient_id']; ?>"
class="btn btn-success">Edit</a>
</td>
<td>
<button type="button" value="<?php echo $cate['patient_id']; ?>"
class="btn btn-danger deletebtn">Delete</a>
</td>
</tr>
<?php
}
} else {
?>
<tr>
<td colspan="9">No Record Found</td>
</tr>
<?php
}
?>
</tbody>
</table>
</div>
</div>
</div>
</div>
</div>
</section>
</div>
<?php include('includes/script.php'); ?>
<script>
$(document).ready(function() {
$('.deletebtn').click(function(e) {
e.preventDefault();
var location_id = $(this).val();
$('.delete_location_id').val(location_id);
$('#DeletModal').modal('show');
});
});
</script>
<?php include('includes/footer.php'); ?>
